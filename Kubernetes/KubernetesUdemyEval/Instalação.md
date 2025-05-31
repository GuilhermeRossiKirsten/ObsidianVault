### **Instalar o kubectl**
https://kubernetes.io/pt-br/docs/tasks/tools/#kubectl

`kubectl version --client`

### **Minikube / Kind**

- permite que você execute o Kubernetes no seu computador local.
- cluster Kubernetes local tudo-em-um ou com vários nós no seu computador pessoal (incluindo PCs Windows, macOS e Linux) para que você possa experimentar o Kubernetes ou para o trabalho de desenvolvimento diário.

`minikube version`

---

###  **Iniciar o Cluster Minikube**

- Usando Docker como driver:
```bash
minikube start --driver=docker
```
 
 O Minikube baixa as imagens necessárias, cria uma VM e configura o Kubernetes local.
 
---
### **Verificar o Status**

```bash
minikube status
```
---
## **Testando o Cluster**

### Verificar nós do cluster:

`kubectl get nodes`

- Deve aparecer algo como:
    
```bash
NAME       STATUS   ROLES                  AGE   VERSION 
minikube   Ready    control-plane,master   Xs   vX.XX.X
```

---
### Criar uma aplicação de teste:

```bash
kubectl create deployment hello-nginx --image=nginx
```
### Verificar a implantação:
```bash
kubectl get all
```
### Expor como serviço:
```bash
kubectl expose deployment hello-nginx --type=LoadBalancer --port=80
```


### Obter URL de acesso:
```bash
minikube service hello-minikube --url
```

Acesse no navegador para verificar se está funcionando.

---

##  **Limpando o Cluster**

- Deletar serviço:
```bash
kubectl delete service hello-minikube
```

- Deletar deployment:
```bash
kubectl delete deployment hello-minikube
```

