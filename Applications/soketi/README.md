# SOKETI

Documentação do Soketi

[https://docs.soketi.app/](https://docs.soketi.app/)

Docker image
[quay.io/soketi/soketi](https://quay.io/repository/soketi/soketi?tab=info)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.CONTAINER_NAME.rule=Host(`HOSTNAME`)"
      - "traefik.http.routers.CONTAINER_NAME.entrypoints=websecure"
      - "traefik.http.services.CONTAINER_NAME.loadbalancer.server.port=6001"
      - "traefik.docker.network=production"
```

Crie o arquivo config/config.json.

```bash
touch config/config.json
```

```json
{
  "debug": false,
  "port": 6001,
  "appManager.array.apps": [
    {
      "id": "app",
      "key": "app",
      "secret": ""
    }
  ]
}
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
