# PROMETHEUS

Documentação do Prometheus

[https://prometheus.io/docs/](https://prometheus.io/docs/)

Docker image

[prom/prometheus](https://hub.docker.com/r/prom/prometheus)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      # Habilita descoberta do container
      - "traefik.enable=true"
      # Habilita a rota do traefik
      - "traefik.http.routers.prometheus.rule=Host(`prometheus.yourdomain.com.br`)"
      - "traefik.http.routers.prometheus.entrypoints=websecure"
      # Habilita o service do traefik (Exposer a porta interna do prometheus)
      - "traefik.http.services.prometheus.loadbalancer.server.port=9090"
      # Habilita o middleware de segurança
      - "traefik.http.middlewares.prometheus-auth.basicauth.users=admin:$$2y$05$$CWW9TIuG4ZlK9RtBnoObYengW8/TImy7Cqfd5T0sPJpbpb0O9bCtG"
      - "traefik.http.routers.prometheus.middlewares=prometheus-auth"
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
