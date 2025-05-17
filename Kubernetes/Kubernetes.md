
Requisitos

Kind -> cria ambiente de execução local do kubernetes https://kind.sigs.k8s.io/
Kubectl -> interface para realizar as operacoes do kubernetes https://kubernetes.io/
docker -> gerenciador dos containers  https://docs.docker.com/



sudo kind create cluster

gera um container no docker para execucao do kubernetes -> docker ps -a

sudo kubectl cluster-info --context kind-kind

mostra as informaçoes do cluster

sudo kubectl get nodes

