# MAILU

Documentação do Mailu

[https://mailu.io/](https://mailu.io/)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.mail.rule=Host(`mail.seudominio.com`)"
      - "traefik.http.routers.mail.entrypoints=websecure"
      - "traefik.http.services.mail.loadbalancer.server.port=80"
      - "traefik.docker.network=production"
```

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
# Basic configuration
MAILU_VERSION=1.9
ROOT=/
DOMAIN=seudominio.com
HOSTNAMES=mail.seudominio.com
TLS_FLAVOR=letsencrypt

# Authentication
AUTH_RATELIMIT=10/minute
ADMIN=admin
PASSWORD=senha_segura

# Network
WEBMAIL=roundcube
REDIS_HOST=redis
REDIS_PASSWORD=suaSenhaSeguraAqui
ANTISPAM=none

# Traefik? Use isso para não expor 80/443 diretamente
# Uncomment if using traefik
# FORWARDED_ALLOW_IPS=*

# Optional DKIM
DKIM_SELECTOR=mail
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
