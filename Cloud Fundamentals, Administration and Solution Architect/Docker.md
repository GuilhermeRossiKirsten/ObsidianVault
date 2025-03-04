
## Introdução

Docker é uma plataforma de criação, distribuição e execução de containers, proporcionando portabilidade e eficiência na execução de aplicações

---
# Virtualização

### Tipos

- **Máquina Virtual (H-based)**: Cada VM tem seu próprio sistema operacional e kernel.
    
- **Container (OS-based)**: Compartilham o mesmo kernel do sistema operacional, sendo mais leves e rápidos.

# Virtualização vs Containers

- **Virtualização por Máquina Virtual (H-based)**
	- Cada VM tem seu próprio SO, Kernel e bibliotecas.
	- Requer mais espaço e tempo para inicialização
	- Exemplo: VMware, VirtualBox, Hyper-V

- **Virtualização por Containers (OS-based)**
	- Compartilham o kernel do SO hospedeiro
	- Mais leves e rápidos que VMs
	- Exemplo: Docker

![[Virtual Machines vs Container Virtualization]]
## Comparação 

| Característica     | VM       | Container     |
| ------------------ | -------- | ------------- |
| Desempenho         | Limitado | Nativo        |
| Consumo de memória | Alto     | Baixo         |
| Tempo de boot      | Minutos  | Milissegundos |

## Vantagens e Benefícios no uso do docker

- Portabilidade
- Flexibilidade
- Escalonamento
- Disponibilidade
- Velocidade
---

## Componentes do Docker

- **Docker Engine**: Motor principal do Docker.
- **Docker Daemon**: Serviço que gerencia containers.
- **Docker CLI**: Interface de linha de comando.
- **Docker Image**: Modelo imutável para containers.
- **Docker Container**: Instância de uma imagem.
- **Dockerfile**: Script para criação de imagens.
- **Docker Compose**: Gerencia múltiplos containers.
- **Docker Hub**: Repositório de imagens.
- **Docker Swarm**: Gerenciamento nativo de clusters Docker.
- **Docker Registry**: Repositório para armazenar imagens Docker.
- **Docker Volumes**: Solução para armazenamento persistente.

---

## Como Funciona o Docker?

Os containers no Docker funcionam como unidades isoladas de disco, memória, processamento e rede, acessando diretamente o SO hospedeiro. Isso permite ambientes distintos coexistirem na mesma máquina sem conflitos.

Os containers são construídos com recursos do kernel do Linux, como:

- **Namespaces**: Isolam processos dentro do container.
- **Cgroups**: Controlam uso de CPU e memória.
- **Chroot**: Define diretórios raiz para segurança.

Além disso, o **Docker Registry** é um repositório na nuvem que facilita o armazenamento e compartilhamento de imagens de containers.

Para gerenciar múltiplos containers, utiliza-se o **Docker Compose**, simplificando a orquestração e implantação automatizada.

Passos básicos:

1. **Criar um Dockerfile** com definições do ambiente.
2. **Construir a imagem**: `docker build -t minha-imagem .`
3. **Rodar um container**: `docker run -d -p 8080:80 minha-imagem`
4. **Gerenciar containers**: `docker ps`, `docker stop <id>`, `docker rm <id>`
5. **Usar Docker Compose** para gerenciar aplicações com múltiplos containers.
6. **Persistir dados** utilizando volumes Docker.

---

##  Persistência de Dados

- **Bind Mounts**: Mapeiam diretórios entre host e container.
- **Volumes**: Método preferido, gerenciado pelo Docker.
- **Tmpfs**: Armazena dados em memória (não persistente).

### Benefícios do uso de volumes:

- Permite backup e migração de dados.
- Maior segurança no compartilhamento de dados entre containers.
- Melhor desempenho e gerenciamento automatizado pelo Docker.

---

##  Segurança

- Controle de acesso: **DAC** (Discricionário) e **MAC** (Obrigatório).
- Restrições entre containers e kernel do SO.
- Atualização e auditoria de imagens.
- Controle de acesso obrigatório (MAC) protege arquivos sensíveis.
- Controle de segurança entre containers para evitar vulnerabilidades.

# MAC vs. DAC - Controle de Acesso

Em sistemas de segurança, existem dois modelos principais de controle de acesso:

1. **DAC (Discretionary Access Control)** – Controle Discricionário
2. **MAC (Mandatory Access Control)** – Controle Obrigatório

Cada um possui características distintas e é utilizado em diferentes cenários, dependendo da necessidade de segurança e flexibilidade.

## DAC - Discretionary Access Control (Controle de Acesso Discricionário)

O **DAC** permite que **o dono do recurso** defina quem pode acessá-lo e em que nível (leitura, escrita, execução).

### **Características:**

- Baseado em **listas de controle de acesso (ACLs)** e permissões padrão (como `chmod` no Linux).
- **Usuário proprietário tem controle total** sobre seus arquivos.
- **Mais flexível, mas menos seguro**, pois usuários podem conceder permissões indevidas.

### **Exemplo no Linux:**

```sh
chmod 755 meu-arquivo.txt  # Dono pode ler, escrever e executar; outros podem apenas ler e executar.
chown user1 meu-arquivo.txt  # Define 'user1' como dono do arquivo.
```

Neste caso, **o dono do arquivo decide quem pode acessá-lo**.

## MAC - Mandatory Access Control (Controle de Acesso Obrigatório)

O **MAC** não permite que usuários decidam livremente sobre permissões. As regras são definidas por **administradores** e aplicadas pelo sistema operacional.

### **Características:**

- **Mais seguro**, pois as permissões são controladas por políticas fixas.
- **Usado em sistemas críticos**, como servidores governamentais e bancos.
- Implementado por sistemas de segurança como **SELinux (Security-Enhanced Linux)** e **AppArmor**.

### **Exemplo no SELinux (Linux com MAC ativado):**

```sh
ls -Z meu-arquivo.txt  # Mostra os rótulos de segurança do arquivo.
```

No MAC, **nem o dono do arquivo pode alterar suas permissões sem autorização do administrador**.

## Comparação: MAC vs. DAC

|Característica|DAC (Discretionary)|MAC (Mandatory)|
|---|---|---|
|**Quem controla o acesso?**|Usuário dono do arquivo|Administrador do sistema|
|**Flexibilidade**|Alta (usuários definem permissões)|Baixa (regras fixas e centralizadas)|
|**Segurança**|Menos seguro (pode ser explorado por malware)|Muito seguro (proteção contra acessos indevidos)|
|**Uso comum**|PCs pessoais, ambientes corporativos comuns|Servidores, sistemas críticos (bancos, defesa, governamental)|

- **DAC** é mais **fácil de usar**, mas **menos seguro**.
- **MAC** é mais **seguro**, mas **menos flexível**.
- **Para ambientes Docker e containers**, o MAC pode ser usado para restringir acesso entre containers e o sistema operacional hospedeiro.

---
##  Instalação do Docker

### Windows

1. Baixe o Docker em: `https://download.docker.com/win/beta/InstallDocker.msi`
2. Verifique se a virtualização está habilitada.
3. Habilite o Hyper-V no Windows.

### Linux (Ubuntu)

```sh
sudo apt update && sudo apt upgrade
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo docker -v
```

### MacOS

1. Baixe em: `https://download.docker.com/mac/beta/Docker.dmg`
2. Instale e execute `Docker.app`.
3. Verifique a versão instalada:

```sh
docker --version
docker-compose --version
docker-machine --version
```

---
## Alguns comandos do Docker 
![[Docker.canvas]]

---
## Docker e Microsserviços

- Containers facilitam a modularização e escalabilidade.
- Microsserviços podem ser independentes e se comunicar via APIs.
- **Arquitetura monolítica** → difícil escalar.
- **Arquitetura de microsserviços** → escalabilidade flexível.

![[Monolith vs Microservices]]

---

# Armazenamento no Docker

## Introdução

Os containers Docker utilizam um sistema baseado em **layers (camadas)** para gerenciar arquivos e persistência de dados. Cada container tem uma camada **writable** (gravável) que é excluída ao remover o container, enquanto as imagens subjacentes permanecem inalteradas.

Para garantir a persistência de dados no Docker, utilizam-se **storage drivers** e diferentes métodos de armazenamento.

---

## Estrutura de Armazenamento no Docker

### **1. Imagens e Layers**

- Uma **imagem** do Docker é composta por várias camadas.
- Cada layer representa uma instrução do **Dockerfile**.
- Quando um container é criado, ele adiciona uma camada **writable** para armazenar modificações.

### **2. Containers e Layers**

- A principal diferença entre uma **imagem** e um **container** é que o container tem uma camada **writable**.
- Todas as alterações feitas no container ficam nessa camada.
- Quando o container é removido, essa camada writable também é excluída.

### **3. Storage Drivers (Drivers de Armazenamento)**

- Gerenciam como os dados são gravados na camada writable.
- Utilizam a tecnologia **Copy-on-Write (CoW)**, evitando duplicação desnecessária de dados.

---

## Métodos de Persistência de Dados

### **1. Montagens de Ligação (Bind Mounts)**

- Ligam um diretório do **host** diretamente a um container.
- Permitem acesso em qualquer lugar no host.
- Dependem do sistema de arquivos do host.
- **Risco:** podem ser alterados por outros aplicativos do sistema.

### **2. Montagens tmpfs (Temporary Filesystem Mounts)**

- Armazena dados na memória RAM do host.
- **Vantagem:** rápido e eficiente para dados temporários.
- **Desvantagem:** os dados são perdidos quando o container é reiniciado.

### **3. Volumes (Método Preferido)**

- Gerenciados pelo próprio Docker.
- Armazenados em um diretório específico no host.
- **Vantagens:**
    - Funcionam em **Linux e Windows**.
    - **Fáceis de migrar e fazer backup**.
    - **Mais seguros** para compartilhamento entre containers.
    - Permitem armazenar volumes em **nuvem ou hosts remotos**.
    - Melhor desempenho, pois não aumentam o tamanho do container.

---

## Criando um banco da dados postgresql com docker

```bash
docker run -p 5432:5432 -d \
-e POSTGRES_USER="fiap" \
-e POSTGRES_PASSWORD="fiap" \
-e POSTGRES_DB="fiap_db" \
--name pg-container \
postgres
```


---
# Docker Compose

O **Docker Compose** é um gerenciador de containers que permite executar múltiplos containers como um único serviço. Ele simplifica o gerenciamento de aplicações compostas por vários containers, como um servidor web e um banco de dados.

---

## Como Funciona?

O Docker Compose utiliza um **arquivo de configuração YAML** chamado `docker-compose.yml`. Nele, definimos:

- Quais containers serão iniciados.
- Variáveis de ambiente.
- Portas expostas.
- Volumes de armazenamento.
- Rede de comunicação entre os containers.

Isso permite iniciar toda a aplicação com **um único comando**:

```sh
docker-compose up -d
```

---

## Exemplo de Arquivo `docker-compose.yml`

```yaml
version: "3.7"
services:
  web:
    image: wordpress
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user
      WORDPRESS_DB_PASSWORD: senha
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: senha
      MYSQL_DATABASE: wordpress
```

Neste exemplo:

- O serviço **web** roda o WordPress e está acessível na porta 8080.
- O serviço **db** roda o MySQL e se conecta ao WordPress.

---

## Estrutura do Arquivo Compose

### **1. Definição da Versão**

```yaml
version: "3.7"
```

Especifica a versão do Docker Compose.

### **2. Definição de Serviços**

```yaml
services:
  web:
    image: wordpress
```

Define os containers que serão criados.

### **3. Configuração de Contexto e Build**

```yaml
  app:
    build:
      context: ./app
      dockerfile: Dockerfile
```

Especifica um caminho para construir a imagem personalizada.

### **4. Configuração de Portas**

```yaml
  web:
    ports:
      - "8080:80"
```

Mapeia a porta do container para o host.

### **5. Definição de Variáveis de Ambiente**

```yaml
  db:
    environment:
      MYSQL_ROOT_PASSWORD: senha
```

Configura credenciais e parâmetros do container.

### **6. Uso de Volumes**

```yaml
  web:
    volumes:
      - ./html:/var/www/html
```

Permite persistência de dados entre o host e o container.

---

# Serverless Computing

## O que é Serverless Computing?

**Serverless Computing** é um modelo de computação em nuvem que permite criar e executar aplicativos sem necessidade de gerenciar servidores.

- Utiliza serviços de **BaaS (Back-end as a Service)** e **FaaS (Functions as a Service)**.
- O código roda em **containers gerenciados** por provedores de nuvem.
- Exemplo de ferramentas: AWS Lambda, Azure Functions, Google Cloud Functions.

---

## Benefícios da Arquitetura Serverless

 **Redução de custos** – Cobra apenas pelos recursos usados (**pay-per-use**). 
 **Alta escalabilidade** – Ajusta automaticamente a capacidade conforme a demanda. 
 **Menos administração** – Elimina a necessidade de configurar servidores. 
 **Maior disponibilidade** – Os provedores garantem alta resiliência e tolerância a falhas.

---

## Desvantagens do Serverless

 - **Dificuldade no debugging e testes**. 
 - **Timeout de execução** – Funções geralmente possuem limite de tempo (~300s). 
 - **Dependência de fornecedor** – Usa APIs e serviços específicos do provedor. 
 - **Cold Starts** – Primeira execução pode ser lenta se a função estiver inativa.
 
## Principais Provedores de Serverless

| Categoria         | Amazon AWS             | Azure           | Google Cloud    |
| ----------------- | ---------------------- | --------------- | --------------- |
| **Computação**    | AWS Lambda             | Azure Functions | Cloud Functions |
| **Armazenamento** | Amazon S3              | Azure Storage   | Cloud Storage   |
| **Mensageria**    | Amazon SQS, Amazon SNS | Service Bus     | Cloud Pub/Sub   |
| **Proxy de API**  | AWS API Gateway        | API Management  | Cloud Endpoints |

**AWS Lambda** é pioneiro e permite executar código sem provisionar servidores, com suporte a diversas linguagens e integração com API Gateway.


---

# Rede de Distribuição de Conteúdo (CDN)

## O que é uma CDN?

A **Rede de Distribuição de Conteúdo** (_Content Delivery Network - CDN_) é um grupo de servidores distribuídos geograficamente que trabalham juntos para fornecer uma entrega rápida de conteúdo da Internet. Atualmente, a maioria do tráfego da web passa por CDNs, incluindo grandes sites como **Facebook, Netflix e Amazon**.

## Benefícios do uso de CDNs

- **Armazenamento em cache**: Reduz custos de largura de banda e evita interrupções no serviço.
- **Aumento da segurança**: Protege sites e e-commerces com melhorias nos certificados de segurança, mitigação de ataques _DDoS_ (_Distributed Denial of Service_) e outras otimizações.
- **Melhoria no tempo de carregamento**: Distribui o conteúdo mais próximo dos visitantes por meio de servidores CDN localizados em _Pontos de Presença_ (_POP - Point of Presence_).
- **Aumento da disponibilidade e redundância**: A natureza distribuída das CDNs permite lidar com alto tráfego e resistir a falhas de hardware.

## Aplicabilidade das CDNs

Para atender à alta demanda de consumo de conteúdo web, as empresas utilizam CDNs para otimizar:

- **Conteúdo estático e dinâmico**;
- **Conteúdo móvel**;
- **Transações de e-commerce**;
- **Distribuição de vídeo, voz e jogos**.



![[ON - CLOU - 07 - Docker_RevFinal.pdf]]