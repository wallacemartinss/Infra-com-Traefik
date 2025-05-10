# POSTGRESQL

Documentação do PostgreSQL

[https://www.postgresql.org/docs/](https://www.postgresql.org/docs/)

Docker Image

[pgvector/pgvector](https://hub.docker.com/r/pgvector/pgvector)

[prometheuscommunity/postgres-exporter](https://hub.docker.com/r/prometheuscommunity/postgres-exporter)

## Usage

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
# Configuração do PostgreSQL
POSTGRES_DB=youdatabasename
POSTGRES_USER=administrator
POSTGRES_PASSWORD=yourpassword

# Configuração do PostgreSQL Exporter
DATA_SOURCE_NAME=postgresql://administrator:yourpassword@postgres:5432/youdatabasename?sslmode=disable
```

## Comands

```bash
docker compose build
```

```bash
docker compose up -d
```

```bash
docker compose down
```

```bash
docker compose rm
```
