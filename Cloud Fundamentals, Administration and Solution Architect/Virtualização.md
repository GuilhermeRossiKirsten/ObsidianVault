## O que é Virtualização?

A virtualização permite criar ambientes virtuais para executar sistemas operacionais, armazenamentos e redes em um único hardware físico. Essa tecnologia é essencial para otimizar o uso de recursos, aumentar a segurança e reduzir custos operacionais.

## Como Funciona?

Uma camada de software (Hypervisor) gerencia a divisão dos recursos de hardware entre as Máquinas Virtuais (VMs) ou Containers. O Hypervisor permite que múltiplos sistemas operacionais sejam executados simultaneamente, isolando os processos para garantir maior estabilidade e segurança.

### Tipos de Virtualização

- **Aplicativos**: Execução remota (ex: Google Stadia, Microsoft Azure Virtual Desktop).
- **Máquinas Virtuais (H-based)**: Cada VM possui seu próprio sistema operacional e kernel, podendo executar diferentes SOs no mesmo hardware.
- **Containers (OS-based)**: Compartilham o mesmo kernel do sistema operacional hospedeiro, proporcionando maior eficiência e rapidez.
- **Virtualização de Armazenamento**: Cria um armazenamento abstrato, unificando vários dispositivos físicos.
- **Virtualização de Rede**: Simula redes físicas, permitindo conexões dinâmicas e seguras.

### Comparativo VM vs Container

| Característica  | VM       | Container |
| --------------- | -------- | --------- |
| Desempenho      | Menor    | Maior     |
| Inicialização   | Minutos  | Segundos  |
| Isolamento      | Completo | Parcial   |
| Uso de Recursos | Alto     | Baixo     |
| Portabilidade   | Menor    | Maior     |

## Hypervisors: Gerenciadores de Virtualização

- **Monolítico**: Gerencia direto no hardware (ex: VMware ESXi, KVM).
- **Microkernelizado**: Necessita de um SO base (ex: Hyper-V, Xen).
- **Type 1 (Bare-Metal)**: Executado diretamente no hardware, garantindo maior desempenho.
- **Type 2 (Hosted)**: Instalado sobre um sistema operacional existente, mais flexível, mas com desempenho reduzido.

## Benefícios da Virtualização

- **Redução de custos** e consumo de energia.
- **Escalabilidade** e flexibilidade no uso de recursos.
- **Ambientes de testes** seguros e eficientes.
- **Segurança**: Isolamento entre as VMs evita contaminação.
- **Facilidade de Backup e Restauração**: Snapshots permitem recuperar rapidamente o estado do sistema.
- **Alta Disponibilidade e Disaster Recovery**: Sistemas virtualizados podem ser replicados para manter a continuidade dos serviços.

## Modos de Rede na Virtualização

|Modo de Rede|Características|
|---|---|
|**Host-Only**|Rede privada entre host e VMs.|
|**NAT**|VMs acessam a Internet via IP do host.|
|**Bridged**|VMs possuem IP próprio na rede.|
|**Overlay Network**|Criada para comunicação segura entre containers distribuídos.|

## Dicas Finais

- **Snapshots**: Criam pontos de restauração das VMs.
- **Pastas Compartilhadas**: Facilitam a troca de arquivos.
- **Manter Hypervisors Atualizados**: Melhor desempenho e segurança.
- **Configuração de CPU e Memória**: Ajuste adequado para otimização de desempenho.
- **Monitoramento e Gerenciamento**: Ferramentas como Prometheus, Grafana e vSphere ajudam no controle dos recursos.

---



![[ON - CLOU - 01 - Virtualização_RevFinal.pdf]]