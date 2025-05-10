# WHATSMEOW

Documentação do Whatsmeow

[https://pkg.go.dev/go.mau.fi/whatsmeow](https://pkg.go.dev/go.mau.fi/whatsmeow)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.CONTAINER_NAME.rule=Host(`HOSTNAME`)"
      - "traefik.http.routers.CONTAINER_NAME.entrypoints=websecure"
      - "traefik.http.services.CONTAINER_NAME.loadbalancer.server.port=80"
      - "traefik.docker.network=production"
```

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
# Ambiente de execução
WHATSAPP_ENV=production

# Nome do bot ou identificação (caso você modifique o exemplo futuramente)
BOT_NAME=WhatsMeowBot

# Diretório de sessão (mantido para referência, embora o binário use ./storage fixo)
SESSION_DIR=/app/storage

# Log level (futuramente você pode passar isso via flags ou customização)
LOG_LEVEL=info

# API Key fictícia (caso use com algum serviço externo como webhook ou proxy reverso com auth)
API_KEY=changeme
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
