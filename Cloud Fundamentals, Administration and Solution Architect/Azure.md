
## O que é o Azure?

Microsoft Azure é uma plataforma de computação em nuvem que oferece serviços como computação, armazenamento, rede e aplicativos. Permite escalabilidade e flexibilidade sem necessidade de hardware próprio.

## Principais Serviços do Azure

### 1. **Computação**

- **Azure Virtual Machines (VMs)**: Hospedagem de Windows/Linux.
- **Azure App Services**: Hospedagem para aplicativos web e APIs.
- **Azure Kubernetes Service (AKS)**: Gerenciamento de contêineres.

### 2. **Armazenamento**

- **Azure Blob Storage**: Armazenamento de objetos.
- **Azure Files**: Compartilhamento de arquivos na nuvem.
- **Azure SQL Database**: Banco de dados relacional gerenciado.

### 3. **Rede**

- **Azure Virtual Network (VNet)**: Redes privadas na nuvem.
- **Azure Load Balancer**: Distribui tráfego entre instâncias.
- **Azure ExpressRoute**: Conexão privada entre Azure e infraestrutura local.

## Criando uma VM no Azure

### 1. Criar Grupo de Recursos:

```bash
az group create --name meu-grupo --location brazilsouth
```

### 2. Criar uma VM Linux:

```bash
az vm create \
  --resource-group "meu-grupo" \
  --name "MinhaVM" \
  --image "UbuntuLTS" \
  --admin-username "admin" \
  --admin-password "SenhaForte@123" \
  --location brazilsouth
```

### 3. Conectar-se via SSH:

```bash
ssh admin@IP_DA_VM
```

### 4. Gerenciamento da VM:

- **Parar VM:**

```bash
az vm stop --resource-group meu-grupo --name MinhaVM
```

- **Iniciar VM:**

```bash
az vm start --resource-group meu-grupo --name MinhaVM
```

- **Excluir Grupo de Recursos (e todos os recursos dentro dele):**

```bash
az group delete --name meu-grupo --no-wait --yes
```

## Azure Cloud Shell

Ferramenta baseada na web para gerenciar recursos do Azure via linha de comando. Acesse: [https://shell.azure.com/bash](https://shell.azure.com/bash)


![[ON - CLOU - 05 - Azure_RevFinal.pdf]]