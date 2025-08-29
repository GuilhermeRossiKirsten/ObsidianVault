---
tags:
  - Docker
---
# Comandos Essenciais do Docker

## 1. Executando o Primeiro Container

Para verificar se o Docker está instalado corretamente, execute:

```sh
docker run hello-world
```

Este comando baixa a imagem `hello-world` (se ainda não estiver no seu sistema) e executa um container que exibe uma mensagem de confirmação.

## 2. Nomeando Containers e Entendendo Diferentes Execuções

### Executando um Container com um Nome Personalizado

Por padrão, o Docker atribui nomes aleatórios aos containers. Você pode especificar um nome usando a flag `--name`:

```sh
docker run --name mynginx nginx
```

### Executando um Container em Segundo Plano (`-d`)

Para executar um container em modo "detached" (segundo plano), use a flag `-d`:

```sh
docker run -d --name mynginx nginx
```

### Mapeando Portas com a Flag `-p`

Para mapear a porta do container para a porta do host, use `-p`:

```sh
docker run -d -p 8080:80 nginx
```

Isso mapeia a porta `80` do container para a porta `8080` do host.

## 3. Parando, Iniciando e Removendo Containers

### Listando Containers em Execução e Parados

Containers em execução:

```sh
docker ps
```

Todos os containers (incluindo parados):

```sh
docker ps -a
```

### Parando um Container

```sh
docker stop mynginx
```

### Iniciando um Container Parado

```sh
docker start mynginx
```

### Removendo um Container

Remoção normal:

```sh
docker rm mynginx
```

Remoção forçada (para containers em execução):

```sh
docker rm -f mynginx
```

## 4. Attach e Detach

### Conectando-se a um Container em Execução (`docker attach`)

```sh
docker attach mynginx
```

Este comando conecta seu terminal ao processo principal do container.

### Saindo do Container sem Parar (`CTRL + P`, `CTRL + Q`)

Para sair do modo `attach` sem parar o container, pressione `CTRL + P` seguido de `CTRL + Q`.

## 5. Executando Comandos e Removendo Containers Automaticamente

### Executando Comandos em um Novo Container

```sh
docker run nginx ls -la
```

Isto executa `ls -la` no container `nginx` e exibe o resultado no seu terminal.

### Entrando no Container com Bash

```sh
docker run -it nginx bash
```

Isto inicia um container `nginx` e abre uma sessão interativa do `bash`.

### Diferença entre `docker run` e `docker exec`

- `docker run`: Cria e inicia um novo container.
- `docker exec`: Executa um comando em um container já em execução.

Exemplo com `docker exec`:

```sh
docker exec -it mynginx bash
```

### Removendo Containers Automaticamente (`--rm`)

```sh
docker run --rm nginx ls -la
```

## 6. Removendo Todos os Containers com Subcomandos

Para remover todos os containers parados:

```sh
docker rm $(docker ps -a -q)
```

Para remover todos os containers, incluindo os em execução, use:

```sh
docker rm -f $(docker ps -a -q)
```

## 7. Publicação de Portas

Para executar um servidor Nginx em um container e publicar a porta:

```sh
docker run -d -p 8080:80 nginx
```

Agora, o Nginx está acessível em `http://localhost:8080`.

## 8. Execução Interativa e Acesso ao Shell

### Acessando o Shell de um Container com `docker exec -it`

Se você já tem um container em execução e deseja acessar seu shell:

```sh
docker exec -it mynginx bash
```

### Diferença entre `docker exec` e `docker attach`

- `docker exec`: Executa um novo processo dentro de um container em execução (ex.: abrir uma nova sessão bash).
- `docker attach`: Anexa seu terminal ao processo principal do container (ex.: ver logs em tempo real).

## Resumo dos Comandos

### Executar um container:

```sh
docker run [opções] imagem [comando]
```

### Listar containers:

```sh
docker ps        # Em execução
docker ps -a     # Todos
```

### Parar, iniciar e remover containers:

```sh
docker stop <nome|id>
docker start <nome|id>
docker rm <nome|id>
docker rm -f <nome|id>   # Forçado
```

### Executar comandos em containers:

```sh
docker exec -it <nome|id> <comando>
```

### Acessar shell bash:

```sh
docker exec -it <nome|id> bash
```

### Remover todos os containers:

```sh
docker rm $(docker ps -a -q)
docker rm -f $(docker ps -a -q)   # Incluindo em execução
```
