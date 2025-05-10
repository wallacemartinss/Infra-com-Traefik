# MYSQL

Documentação do MySQL

[https://dev.mysql.com/doc/](https://dev.mysql.com/doc/)

Docker Image

[mysql](https://hub.docker.com/_/mysql)

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

Crie o arquivo conf/conf-my.cnf

```
[mysqld]
bind-address = 0.0.0.0
default_authentication_plugin=mysql_native_password
character-set-server=utf8mb4
collation-server=utf8mb4_unicode_ci
slow_query_log=1
long_query_time=1
log_output=FILE
max_connections=400
```

Crie o arquivo conf/init.sql

```bash
touch conf/init.sql
```

Lembre de ajustar a senha igual ao do arquivo .env.

```sql
CREATE USER IF NOT EXISTS 'exporter'@'%' IDENTIFIED BY 'MYSQL_EXPORTER_PASSWORD';
GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'%';
FLUSH PRIVILEGES;
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