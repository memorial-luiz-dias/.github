# Memorial Luiz Alberto

Sou desenvolvedora backend e, como toda desenvolvedora, escrevo código para resolver problemas.
Mas este projeto nasceu de uma dor diferente — a de perder um irmão.

Luiz Alberto foi muito mais do que família. Foi luz, foi presença, foi aquele tipo de pessoa que deixa uma marca que o tempo não apaga. E quando ele foi, eu fiquei com as mãos que sabem construir coisas, e com a vontade de construir algo que o mantivesse perto.

Então eu fiz o que sei fazer: escrevi código.

---

Cada tabela criada aqui, cada script, cada linha de SQL carrega um pedaço da intenção de que as memórias dele nunca se percam. Este sistema foi pensado para que a família tenha um lugar onde as lembranças vivem — fotos, histórias, momentos guardados com cuidado, acessíveis para sempre.

A luz dele ainda me ilumina quando eu sento para escrever. E enquanto eu puder escrever, ele continua aqui.

---
## Repositórios

| Repositório | Descrição | Tecnologia |
|---|---|---|
| [projeto-memorial-api](./projeto-memorial-api) | API REST com autenticação e CRUD de memórias | Java 21 + Spring Boot 3 |
| [projeto-memorial-app](./projeto-memorial-app) | Interface web para visualização e envio de memórias | React + TypeScript + Vite |
| [projeto-memorial-database](./projeto-memorial-database) | Scripts SQL de criação e carga inicial do banco | PostgreSQL 16 |

## Requisitos

- [Docker](https://docs.docker.com/get-docker/) e [Docker Compose](https://docs.docker.com/compose/install/)
- Git

## Como subir o projeto

### 1. Clone os repositórios

```bash
git clone <url-do-repositorio>
cd projeto-memorial-luiz-dias
```

### 2. Configure as variáveis de ambiente

```bash
cp .env.example .env
```

Edite o `.env` com suas configurações. Para desenvolvimento local os valores padrão já funcionam.

### 3. Suba todos os serviços

```bash
docker compose up --build
```

| Serviço | URL |
|---|---|
| Frontend | http://localhost:5173 |
| API | http://localhost:8080 |
| Swagger UI | http://localhost:8080/swagger-ui.html |
| Banco de dados | localhost:5432 |

### Subir apenas o banco e a API

```bash
docker compose up db api --build
```

### Parar todos os serviços

```bash
docker compose down
```

### Apagar volumes (resetar banco de dados)

```bash
docker compose down -v
```

## Arquitetura

```
                ┌─────────────────┐
                │  projeto-        │
  Usuário ────> │  memorial-app   │ :5173
                │  (React/Nginx)  │
                └────────┬────────┘
                         │ HTTP
                ┌────────▼────────┐
                │  projeto-        │
                │  memorial-api   │ :8080
                │  (Spring Boot)  │
                └────────┬────────┘
                         │ JDBC
                ┌────────▼────────┐
                │  PostgreSQL 16  │ :5432
                └─────────────────┘
```

## Variáveis de ambiente

| Variável | Descrição | Padrão |
|---|---|---|
| `DB_NAME` | Nome do banco de dados | `memorial_luiz` |
| `DB_USER` | Usuário do banco | `memorial_user` |
| `DB_PASSWORD` | Senha do banco | — |
| `API_PORT` | Porta da API | `8080` |
| `APP_PORT` | Porta do frontend | `5173` |
| `VITE_API_URL` | URL da API usada pelo frontend | `http://localhost:8080` |
