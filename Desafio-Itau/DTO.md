O que é um DTO (Data Transfer Object)?

O **DTO (Data Transfer Object)** é um **objeto usado para transferir dados entre diferentes camadas** da aplicação, geralmente entre o **Controller** e o **Service**.

No nosso caso, o **`TransactionDTO`** é responsável por representar os dados da transação recebidos na requisição **POST /transacao**.

---

###  Por que usar um DTO? 

1. **Evita expor diretamente entidades do banco de dados**
    
    - Como não estamos usando banco neste projeto, isso não é um problema agora, mas em sistemas reais, **expor entidades diretamente pode gerar vulnerabilidades**.

2. **Facilita a validação de dados**
    
    - O **`TransactionDTO`** nos permite usar **anotações do Bean Validation** (`@NotNull`, `@Min(0)`) para garantir que os dados da requisição sejam válidos antes de processá-los.

3. **Garante um formato padronizado de entrada e saída**
    
    - Se tivermos várias APIs consumindo o mesmo sistema, os DTOs ajudam a **padronizar os dados** que entram e saem.

---

###  Diferença entre DTO e Model

- **DTO (`TransactionDTO`)** → Representa apenas os **dados de entrada e saída** da API.
- **Model (Entidade)** → Representaria o **objeto salvo no banco de dados**.
- 
**Exemplo:**  
Imagine que temos um sistema de pedidos. Se um usuário faz uma requisição para criar um pedido, o **DTO conteria apenas os dados necessários para essa requisição**:

```json
{     
	"clienteId": 123,     
	"valorTotal": 250.00 
}
```


Mas o **modelo no banco de dados teria mais informações**, como ID do pedido, status e data de criação:

```json
{     
	"id": 456,     
	"clienteId": 123,     
	"valorTotal": 250.00,     
	"status": "PROCESSANDO",     
	"dataCriacao": "2024-03-20T15:00:00" 
}
```


Ou seja, **DTOs são úteis para manipular apenas os dados necessários** em cada operação.