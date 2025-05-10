# TYPESENSE

Documentação do Typesense

[https://typesense.org/docs/](https://typesense.org/docs/)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.typesense.rule=Host(`typesense.yourdomain.online`)"
      - "traefik.http.routers.typesense.entrypoints=websecure"
      - "traefik.http.services.typesense.loadbalancer.server.port=8108"
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
