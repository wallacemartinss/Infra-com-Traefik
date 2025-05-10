# N8N

Documentação do N8N

[https://docs.n8n.io/](https://docs.n8n.io/)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.CONTAINER_NAME.rule=Host(`HOSTNAME`)"
      - "traefik.http.routers.CONTAINER_NAME.entrypoints=websecure"
      - "traefik.http.services.CONTAINER_NAME.loadbalancer.server.port=5678"
      - "traefik.docker.network=production"
```

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
TYPESENSE_API_KEY=
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
