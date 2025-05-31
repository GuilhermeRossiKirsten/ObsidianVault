
## 1. O que é um **Pod**?

- **Pod** = menor objeto implantável no Kubernetes.
- Encapsula **um ou mais contêineres** que:
    - Compartilham **mesmo namespace de rede** (IP e portas localhost).
    - Compartilham **mesmo(s) volume(s)** para persistência ou troca de dados.
    - São criados e destruídos **juntos**.

---

## 2. Relação **1:1** (Pod ↔ Contêiner)

- **Padrão**: um Pod contém **apenas um** contêiner de aplicação.
- Para **escalar**, **não** adicionamos contêineres a um Pod existente:
- Cada réplica é um **novo Pod** isolado.

```bash
# cria 3 réplicas (Pods) do nginx 
kubectl run nginx --image=nginx --replicas=3`
```

---

## 3. **Escalabilidade**

1. **Dentro** do mesmo Nó:    
    - Kubernetes agenda novas réplicas de Pod no nó até esgotar recursos.
2. **Em múltiplos Nós**:
    - Se o nó atual estiver sem capacidade, o Scheduler aloca novos Pods em outros nós do cluster.
3. **Horizontal Pod Autoscaler**
    - Ajusta réplicas de Pods automaticamente com base em métricas (CPU, memória, etc.).
```bash

kubectl autoscale deployment my-app --min=2 --max=10 --cpu-percent=70`

```
---

## 4. **Múltiplos contêineres** num mesmo Pod

- **Use-case**: um “helper” container que deve:
    
    - Compartilhar dados íntimos (mesmo volume).
        
    - Comunicar-se via `localhost`.
        
    - Iniciar e parar junto com o contêiner principal.
        
- **Exemplo de spec**:
```yaml
apiVersion: v1 
kind: Pod 
metadata:   
	name: web-with-sidecar 
spec:   
	containers:   
	- name: app     
	  image: minha-app:latest   
	- name: sidecar     
	  image: meu-helper:latest     
	  volumeMounts:     
		- name: shared-data       
		  mountPath: /data   
	volumes:   
	- name: shared-data     
	  emptyDir: {}
``` 

> 💡 **Observação**: multi-container Pods são um padrão menos comum;  
> na maioria dos casos, use **1 Pod = 1 contêiner**.

---

## 5. Ciclo de vida e **manutenção**

- **Criar** um Pod:
```bash
kubectl run meu-pod --image=redis
```    

- **Listar** Pods:
```bash
kubectl get pods
```    

- **Descrever** detalhes e eventos:
```bash
kubectl describe pod meu-pod
```

- **Ver logs** (contêiner único):
```bash
kubectl logs meu-pod
```

- **Excluir** um Pod:
```bash
kubectl delete pod meu-pod
```
---

## 6. Boas práticas e observações

- Nunca **edite** diretamente Pods gerenciados por um Deployment; altere o Deployment.
- Para **atualizar** a aplicação, use:
```bash
kubectl set image deployment/minha-app minha-app=minha-app:versao2
```
- Evite usar `kubectl run` em produção, prefira **manifests YAML** ou **Helm charts**.
- Planeje sempre **readiness** e **liveness probes** para garantir saúde dos Pods.