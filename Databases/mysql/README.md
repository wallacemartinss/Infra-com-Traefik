# MYSQL

Documentação do MySQL

[https://dev.mysql.com/doc/](https://dev.mysql.com/doc/)

Docker Image

[mysql](https://hub.docker.com/_/mysql)

[quay.io/prometheus/mysqld-exporter](https://quay.io/repository/prometheus/mysqld-exporter?tab=info)

## Usage

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
MYSQL_ROOT_PASSWORD=

MYSQL_EXPORTER_USER=exporter
MYSQL_EXPORTER_PASSWORD=
```

Crie o arquivo conf/init.sql

```bash
cp conf/init.sql.example conf/init.sql
```

Lembre de ajustar a senha igual ao do arquivo .env.

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