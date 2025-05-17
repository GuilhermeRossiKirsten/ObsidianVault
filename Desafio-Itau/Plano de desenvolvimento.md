### **1. Configuração Inicial do Projeto**

- Criar um novo projeto Spring Boot no [Spring Initializr](https://start.spring.io/)
    
    - **Dependências**:  
         Spring Web  
         Lombok (para reduzir boilerplate)  
         Validation (para validação dos dados)
- Estruturar o projeto seguindo boas práticas:

```bash
`src/main/java/com/seuusuario/transacoes/ 
├── controller/       # Controllers para os endpoints 
├── service/          # Lógica de negócios 
├── model/            # Classes de modelo (DTOs) 
├── repository/       # Armazena as transações em memória 
├── dto/              # Objetos para requisição/resposta 
├── config/           # Configurações opcionais 
├── exception/        # Classes para tratamento de erro 
├── utils/            # Métodos auxiliares`

```

---

### **2. Implementação dos Endpoints**

####  **POST /transacao** – Receber transações

- Criar DTO `TransactionDTO` com `valor` e `dataHora`
- Implementar validações:
    - `valor` deve ser >= 0
    - `dataHora` deve estar no passado
- Salvar a transação em uma `List<Transaction>` na memória
- Responder com:
    - `201 Created` se a transação for válida
    - `422 Unprocessable Entity` se for inválida
    - `400 Bad Request` se o JSON for malformado

####  **DELETE /transacao** – Limpar todas as transações

- Simplesmente limpar a lista em memória e retornar `200 OK`

####  **GET /estatistica** – Retornar estatísticas

- Filtrar transações dos últimos **60 segundos**
- Calcular:
    - `count`, `sum`, `avg`, `min`, `max`
- Retornar `200 OK` com o JSON esperado

---

### **3. Testes Automatizados**

- Usar **JUnit e Mockito** para:  Testes unitários dos serviços  
     Testes de integração dos endpoints

---

### **4. Melhorias Extras**

- ** Logs**: Configurar logs com **SLF4J**
- ** Health Check**: Criar endpoint `/health` para verificar a API
- ** Docker**: Criar um `Dockerfile` para rodar o projeto
- ** Swagger**: Documentação interativa da API

---

## **Dicas**

1️⃣ **Use `OffsetDateTime`** para manipular a data corretamente  
2️⃣ **Crie um `@Service` para a lógica de negócios** em vez de colocar tudo no Controller  
3️⃣ **Use `@Valid` e `@ExceptionHandler`** para lidar com validações automaticamente  
4️⃣ **Implemente um `@Scheduled` para limpar transações antigas** se quiser um extra