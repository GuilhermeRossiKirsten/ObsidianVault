
## Introdução

Kubernetes (K8s) é uma plataforma de código aberto para orquestração de containers. Criado pelo Google e mantido pela CNCF, ele gerencia a execução de aplicações containerizadas em clusters distribuídos, garantindo escalabilidade, disponibilidade e automação.

## Principais Características

- **Orquestração de Containers:** Automatiza a implantação, escalonamento e operação de aplicações em containers.
- **Autoescalação:** Ajusta automaticamente o número de containers com base na carga.
- **Gerenciamento de Recursos:** Controla CPU, memória e rede de maneira eficiente.
- **Alta Disponibilidade:** Replica containers para garantir resiliência e recuperação automática.
- **Portabilidade:** Funciona em ambientes híbridos (on-premise e cloud).
- **Suporte a Diversos Runtimes:** Docker, containerd e CRI-O.

---

## Arquitetura do Kubernetes

### Componentes Principais

1. **Control Plane (Plano de Controle)**
    
    - **API Server:** Exposição da API REST do Kubernetes.
    - **Etcd:** Banco de dados chave-valor que armazena o estado do cluster.
    - **Controller Manager:** Controla estados desejados, como replicação e balanceamento.
    - **Scheduler:** Aloca workloads nos nós disponíveis do cluster.
    
2. **Nodes (Nós de Execução)**
    
    - **Kubelet:** Agente que garante a execução dos containers.
    - **Kube-Proxy:** Gerencia regras de rede e balanceamento de carga.
    - **Container Runtime:** Motor responsável por executar containers (Docker, containerd, etc.).
    
3. **Objetos do Kubernetes**
    
    - **Pod:** Mínima unidade de execução, contendo um ou mais containers.
    - **Deployment:** Gerencia o ciclo de vida dos Pods e garante a replicação.
    - **Service:** Exposição de aplicações, criando IPs fixos e balanceando tráfego.
    - **ConfigMap e Secret:** Armazenamento de configurações e credenciais.

---

## Funcionamento

1. O usuário define a configuração da aplicação via YAML ou JSON.
2. A configuração é enviada ao **API Server**, que a armazena no **etcd**.
3. O **Scheduler** aloca os Pods nos Nodes disponíveis.
4. O **Kubelet** executa e monitora os Pods.
5. O **Kube-Proxy** gerencia a comunicação entre os serviços.

---

## Comparação com Outras Tecnologias

|Tecnologia|Função|
|---|---|
|**Docker Swarm**|Orquestração nativa do Docker, mais simples, porém menos robusta que o K8s.|
|**OpenShift**|Plataforma baseada em Kubernetes com segurança reforçada e ferramentas adicionais para DevOps.|
|**OpenStack**|Orquestração de infraestrutura de nuvem, enquanto Kubernetes gerencia containers.|

---


### **Primeiros Passos com Kubernetes**

Para iniciar no Kubernetes, siga estes passos:

1. **Instalar o Minikube** (para ambiente local):
    
    ```bash
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
    ```
    
2. **Iniciar um cluster local:**
    
    ```bash
    minikube start
    ```
    
3. **Verificar o status do cluster:**
    
    ```bash
    kubectl cluster-info
    ```
    
4. **Criar um deployment:**
    
    ```bash
    kubectl create deployment hello-world --image=k8s.gcr.io/echoserver:1.4
    ```
    
5. **Expor o deployment para acesso externo:**
    
    ```bash
    kubectl expose deployment hello-world --type=NodePort --port=8080
    ```
    
6. **Obter o URL de acesso:**
    
    ```bash
    minikube service hello-world --url
    ```
    

Esses comandos criam um pequeno ambiente Kubernetes local e iniciam um serviço básico para testes.


![[on-image-papel-kubernetes-docker-swarm.svg]]


![[ON - CLOU - 08 - Kubernetes_RevFinal.pdf]]