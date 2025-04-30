# TYPESENSE

Documentação do Typesense

[https://typesense.org/docs/](https://typesense.org/docs/)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.CONTAINER_NAME.rule=Host(`HOSTNAME`)"
      - "traefik.http.routers.CONTAINER_NAME.entrypoints=websecure"
      - "traefik.http.services.CONTAINER_NAME.loadbalancer.server.port=8108"
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
