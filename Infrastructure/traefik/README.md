# TRAEFIK

Documentação do Traefik

[https://doc.traefik.io/traefik/](https://doc.traefik.io/traefik/)

Docker image

[traefik](https://hub.docker.com/_/traefik)

## Usage

Crie o arquivo secrets/cloudflare-token.secret

```bash
touch secrets/cloudflare-token.secret
```

Crie o arquivo secrets/cloudflare-email.secret

```bash
touch secrets/cloudflare-email.secret
```

Crie o arquivo certs/acme.json

```bash
touch certs/acme.json
```

```json
{
  
}
```

Adicione a permissão ao arquivo certs/acme.json

```bash
chmod 600 -R certs/acme.json
```

Gere a senha usando o htpasswd:

```bash
htpasswd -nbB yourusername yourpassword
```

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      # Acesso ao painel do Traefik
      - "traefik.enable=true"
      - "traefik.http.routers.traefik.rule=Host(`traefik.yourdomain.com.br`)"
      - "traefik.http.routers.traefik.entrypoints=websecure"
      - "traefik.http.routers.traefik.service=api@internal"
      - "traefik.http.middlewares.traefik-auth.basicauth.users=admin:$$2y$05$$P.M7abpqCKXMAUh07Zm8RuDdCx7XoL1D3x3wfN2o.4nJN2n9YZj3O" #senha123
      - "traefik.http.routers.traefik.middlewares=traefik-auth"
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
