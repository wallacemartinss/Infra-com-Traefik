# REDIS

Documentação do Redis

[https://redis.io/docs/](https://redis.io/docs/)

Docker Image

[redis](https://hub.docker.com/_/redis)

[oliver006/redis_exporter](https://hub.docker.com/r/oliver006/redis_exporter)

## Usage

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
REDIS_PASSWORD=
```

Crie o arquivo conf/redis.conf

```bash
cp conf/redis.conf-example conf/redis.conf
```

Lembre de ajustar o **requirepass** a senha igual ao do arquivo .env.

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