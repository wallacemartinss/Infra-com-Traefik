# MINIO

Documentação do Minio

[https://min.io/docs/minio/container/index.html](https://min.io/docs/minio/container/index.html)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"

      # Console Web UI
      - "traefik.http.routers.minio-console.rule=Host(`minio.yourdomain.online`)"
      - "traefik.http.routers.minio-console.entrypoints=websecure"
      - "traefik.http.routers.minio-console.service=minio-console"
      - "traefik.http.services.minio-console.loadbalancer.server.port=9002"

      # API S3
      - "traefik.http.routers.minio-api.rule=Host(`s3.yourdomain.online`)"
      - "traefik.http.routers.minio-api.entrypoints=websecure"
      - "traefik.http.routers.minio-api.service=minio-api"
      - "traefik.http.services.minio-api.loadbalancer.server.port=9000"

      - "traefik.docker.network=production"
```

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
MINIO_ROOT_USER=admin
MINIO_ROOT_PASSWORD=minio123
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
