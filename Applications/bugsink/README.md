# BUGSINK

Documentação do Bugsink

[https://www.bugsink.com/docs/installation/](https://www.bugsink.com/docs/installation/)

Docker image

[bugsink/bugsink](https://hub.docker.com/r/bugsink/bugsink)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.bugsink.rule=Host(`bugsink.seudominio.com`)"
      - "traefik.http.routers.bugsink.entrypoints=websecure"
      - "traefik.http.services.bugsink.loadbalancer.server.port=8000"
      - "traefik.docker.network=production"
```

Crie o arquivo .env.

```bash
cp .env.example .env
```

Gerar o secret_key usando o comando:

```bash
openssl rand -base64 50
```

Atualize as variáveis do .env:

```dotenv
PORT=8000
SECRET_KEY=
DATABASE_URL=mysql://user:password@mysql:3306/bugsink
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