# N8N

Documentação do N8N

[https://docs.n8n.io/](https://docs.n8n.io/)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.n8n.rule=Host(`n8n.yourdomain.com.br`)"
      - "traefik.http.routers.n8n.entrypoints=websecure"
      - "traefik.http.services.n8n.loadbalancer.server.port=5678"
      - "traefik.docker.network=production"
```

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=admin
N8N_HOST=n8n.yourdomain.com.br
N8N_PORT=5678
N8N_PROTOCOL=https
N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true
NODE_ENV=production
TZ=America/Sao_Paulo
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
