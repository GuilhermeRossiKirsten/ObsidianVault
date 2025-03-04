
## 1. Introdução

A Amazon Web Services (AWS) é a maior e mais utilizada plataforma de computação em nuvem do mundo. Ela oferece uma ampla gama de serviços para empresas e desenvolvedores, permitindo escalabilidade, segurança e inovação em aplicações modernas.

## 2. Motivos para Aprender AWS

- **Liderança de mercado:** AWS detém a maior participação no mercado global de cloud computing.
- **Valorização profissional:** Profissionais certificados em AWS possuem alta demanda e salários competitivos.
- **Flexibilidade e inovação:** A AWS permite desenvolvimento ágil e integração com diversas tecnologias.

## 3. Certificações AWS

A AWS oferece várias certificações para diferentes níveis e especializações:

- **Fundamentais:** AWS Certified Cloud Practitioner (CCP).
- **Associate:**
    - AWS Certified Solutions Architect – Projetos de arquitetura em nuvem.
    - AWS Certified Developer – Focado no desenvolvimento de aplicações AWS.
    - AWS Certified SysOps Administrator – Administração de sistemas na AWS.
- **Profissional:**
    - AWS Certified Solutions Architect Professional.
    - AWS Certified DevOps Engineer.
- **Especialidade:** Segurança, Machine Learning, Big Data, Alexa, entre outras.

## 4. Infraestrutura Global

- **Regiões:** 24 regiões distribuídas globalmente.
- **Zonas de Disponibilidade:** 77 datacenters interconectados.
- **Pontos de Presença (PoPs):** 216 locais para otimização de latência e conformidade regulatória.
- **Modelo de segurança:** Redundância e compliance com regulamentações locais.

## 5. Formas de Interação com AWS

- **AWS Management Console:** Interface gráfica para gerenciamento de recursos.
- **AWS CLI (Command Line Interface):** Gerenciamento via linha de comando para automação.
- **AWS SDKs:** Integração programática com linguagens como Python, Java e JavaScript.
- **Infraestrutura como código:** Uso de **AWS CloudFormation** e **Terraform** para automação de recursos.

## 6. Princípios Arquiteturais

A AWS segue boas práticas para construção de infraestruturas seguras e eficientes, baseadas no **AWS Well-Architected Framework**.

### **Seus cinco pilares:**

1. **Excelência operacional** – Automação, monitoramento e melhorias contínuas.
2. **Segurança** – Controle de acessos, criptografia e conformidade regulatória.
3. **Confiabilidade** – Tolerância a falhas e recuperação rápida de desastres.
4. **Eficiência de desempenho** – Uso eficiente de recursos computacionais.
5. **Otimização de custos** – Redução de gastos por meio de monitoramento e escalabilidade.

## 7. Serviços Principais da AWS

### 7.1. **Computação**

- **EC2 (Elastic Compute Cloud):** Máquinas virtuais escaláveis sob demanda.
- **Lambda:** Execução de código serverless, sem necessidade de gerenciar servidores.
- **ECS & EKS:** Gerenciamento de containers Docker e Kubernetes.

### 7.2. **Armazenamento**

- **S3 (Simple Storage Service):** Armazenamento de objetos escalável e seguro.
- **EBS (Elastic Block Store):** Volumes persistentes para EC2.
- **Glacier:** Armazenamento de longo prazo e backup.

### 7.3. **Banco de Dados**

- **RDS (Relational Database Service):** Banco de dados gerenciado (MySQL, PostgreSQL, SQL Server, etc.).
- **DynamoDB:** Banco NoSQL escalável e de baixa latência.
- **Aurora:** Banco de alto desempenho compatível com MySQL e PostgreSQL.

### 7.4. **Redes e Segurança**

- **VPC (Virtual Private Cloud):** Criação de redes isoladas dentro da AWS.
- **IAM (Identity and Access Management):** Controle granular de permissões.
- **CloudFront:** Rede de distribuição de conteúdo (CDN) para baixa latência.
- **AWS WAF e Shield:** Proteção contra ataques cibernéticos.

## 8. Hands-on: Criando uma Instância EC2

### **Passos:**

1. Escolher uma **Amazon Machine Image (AMI)** para a instância.
2. Selecionar o **tipo de instância** (T2, T3, M5, C5 etc.).
3. Configurar detalhes da rede, incluindo **VPC e sub-redes**.
4. Definir o **armazenamento EBS** e configurar snapshots para backup.
5. Adicionar **tags** para organização e rastreamento.
6. Configurar **grupo de segurança** (firewall e regras de acesso).
7. Criar um **par de chaves SSH** para acesso remoto seguro.

### **Automação com AWS CLI:**

- **Configuração inicial:**
    
    ```bash
    aws configure
    ```
    
- **Listar instâncias EC2:**
    
    ```bash
    aws ec2 describe-instances
    ```
    
- **Iniciar uma instância:**
    
    ```bash
    aws ec2 start-instances --instance-ids <ID>
    ```
    
- **Parar uma instância:**
    
    ```bash
    aws ec2 stop-instances --instance-ids <ID>
    ```
    

---


![[ON - CLOU - 04 - Amazon Web Services (AWS)_RevFinal.pdf]]


