# Memorial Luiz Alberto

Projeto criado em homenagem a Luiz Alberto. Uma plataforma onde amigos e familiares podem enviar e visualizar memórias através de fotos, vídeos e histórias.

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
