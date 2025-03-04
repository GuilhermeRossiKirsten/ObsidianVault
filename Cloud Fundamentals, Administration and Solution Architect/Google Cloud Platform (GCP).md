
## O que é o GCP?

O **Google Cloud Platform (GCP)** é a plataforma de computação em nuvem da Google, utilizada por empresas como **PayPal, Twitter, Spotify, Carrefour, Vodafone, FedEx, LG e Airbus**. Ela oferece:

- **Infraestrutura como Serviço (IaaS)**
- **Plataforma como Serviço (PaaS)**
- **Computação Serverless**

O GCP permite que empresas e desenvolvedores utilizem a mesma infraestrutura que suporta produtos da Google, como o **Gmail, YouTube e Google Search**.

---

## Principais Serviços do GCP

### 1. G Suite (Google Workspace)

**Conjunto de ferramentas de produtividade** para uso corporativo, incluindo:

- **Gmail** (e-mail personalizado)
- **Google Meet** (videoconferências)
- **Google Calendar** (calendário compartilhado)
- **Google Drive** (armazenamento em nuvem)
- **Google Docs, Sheets, Keep, Forms e Sites**

Esse serviço é pago, com valores cobrados por usuário/mês.

---

### 2. Google Cloud Storage

Serviço de **armazenamento de objetos** para qualquer tipo de dado, oferecendo alta durabilidade e disponibilidade. Equivalente ao Google Drive, mas voltado para empresas e aplicações escaláveis.

#### Classes de armazenamento:

- **Standard:** Alta frequência de acesso, indicado para dados frequentemente utilizados.
- **Nearline:** Para dados acessados ocasionalmente (mínimo 30 dias de armazenamento).
- **Coldline:** Armazenamento de longo prazo com menor custo (mínimo 90 dias).
- **Archive:** Ideal para backup e arquivamento, com menor custo (mínimo 365 dias).

#### Outros serviços de armazenamento:

- **Persistent Disk:** Discos virtuais para máquinas virtuais no Compute Engine.
- **Cloud Firestore:** Banco de dados NoSQL escalável.

#### Automação com gsutil:

- Criar buckets: `gsutil mb gs://bucket-name`
- Enviar arquivos: `gsutil cp file.txt gs://bucket-name/`
- Listar arquivos: `gsutil ls gs://bucket-name/`

---

### 3. Google Compute Engine (GCE)

Plataforma de **máquinas virtuais (VMs)** e **containers**, permitindo escalabilidade, segurança e personalização.

#### Criando uma VM:

1. Acesse [Google Compute Engine](https://console.cloud.google.com/compute)
2. Clique em "Criar VM"
3. Escolha um sistema operacional (Debian, Ubuntu, Windows, etc.)
4. Configure os recursos (CPU, RAM, disco, rede)
5. Acesse via SSH diretamente pelo navegador

O GCE também suporta **containers**, permitindo implantações otimizadas para Kubernetes e Docker.

---

### 4. Google App Engine (GAE)

Serviço **serverless** para hospedar aplicações sem necessidade de gerenciar infraestrutura.

#### Implantação de uma aplicação:

1. Criar um projeto no [App Engine](https://console.cloud.google.com/appengine)
2. Escolher a região do deploy (us-central, europe-west, etc.)
3. Selecionar a linguagem de desenvolvimento (Python, Node.js, Java, PHP, etc.)
4. Subir o código com `gcloud app deploy`

#### Benefícios do App Engine:

- **Escalabilidade automática**
- **Monitoramento e logs integrados**
- **Integração com bancos de dados e APIs do GCP**
- **Hospedagem de aplicações web sem necessidade de gerenciar servidores**

---

![[ON - CLOU - 06 - GCP_RevFinal.pdf]]