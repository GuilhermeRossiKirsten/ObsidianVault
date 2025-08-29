---
tags:
  - Kubernetes
---

**Kubertenes** (K8s) é um produto Open Source utilizado para automatizar a implantação, o dimensionamento e o gerenciamento de aplicativos em contêiner


---

- Kubernetes é disponibilizado atravéz de um conjunto de APIs
- API utilizando o CLI: **[kubectl](https://kind.sigs.k8s.io/)**
- Tudo é baseado em estados, configuramos o estado de cada objeto
- Kubernetes Master
	- Kube-apiserver
	- Kube-controller-manager
	- Kube-scheduler
- Outros Nodes:
	- Kubelet
	- Kubeproxy



Cria um cluster de kubernetes ( apenas 1 nó)
```bash
kind create cluster
```

Mostra em qual contexto (cluster) estamos...
troca o ambiente de execução do kubernetes
```bash
kubectl cluster-info --context kind-kind

Kubernetes control plane is running at https://127.0.0.1:53791
CoreDNS is running at https://127.0.0.1:53791/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
```

Lista os nodes do cluster de kubernetes
```bash
kubectl get nodes
```

Lista os clusters
```bash
kind get clusters
```

```bash
kubectl config get-clusters
```

Troca o contexto (cluster)
```bash
kubectl config use-context kind-kube
```


```bash
kind create cluster --config .\k8s\kind.yaml
```


```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4

nodes:
- role: control-plane
- role: worker
- role: worker
- role: worker
- role: worker
```

Requisitos

# [Kind](https://kind.sigs.k8s.io/) -> cria ambiente de execução local do kubernetes 
# [Kubectl](https://kubernetes.io/) -> interface para realizar as operacoes do kubernetes
# [docker](https://docs.docker.com/) -> gerenciador dos containers 






---


Cluster - Conjunto de máquinas (Nodes)
Cada máquina possui uma quantidade de vCPU e Memória

Pods - Unidade que contém os containers provisionados,
representa os processos rodando no cluster


