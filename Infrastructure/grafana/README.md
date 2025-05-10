# GRAFANA

Documentação do Grafana

[https://grafana.com/docs/](https://grafana.com/docs/)

Docker image

[grafana/grafana](https://hub.docker.com/r/grafana/grafana)

## Usage

Ajustar o endpoint do traefik no arquivo docker-compose.yml

```yaml
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.grafana.rule=Host(`grafana.yourdomain.com.br`)"
      - "traefik.http.routers.grafana.entrypoints=websecure"
      - "traefik.http.services.grafana.loadbalancer.server.port=3000"
      - "traefik.docker.network=production"
```

Crie o arquivo .env.

```bash
cp .env.example .env
```

```dotenv
# Define usuário admin
GF_SECURITY_ADMIN_USER=youremail@example.com
# Defina uma senha segura
GF_SECURITY_ADMIN_PASSWORD=password
# Domínio usado no Traefik
GF_SERVER_DOMAIN=traefik.yourdomain.com.br
# URL base correta para evitar erros de proxy reverso
GF_SERVER_ROOT_URL=https://grafana.yourdomain.com.br
# Desativa acesso anônimo
GF_AUTH_ANONYMOUS_ENABLED=false
# Mantém o login ativado
GF_AUTH_DISABLE_LOGIN_FORM=false

# Bloco Configuração SMTP
GF_SMTP_ENABLED=true
GF_SMTP_HOST=smtp.seu-servidor.com:587
GF_SMTP_USER=seu-email@seu-dominio.com
GF_SMTP_PASSWORD="$suaSenha123#"
GF_SMTP_FROM_ADDRESS=grafana@seu-dominio.com
GF_SMTP_FROM_NAME="Grafana Alertas"
GF_SMTP_SKIP_VERIFY=true
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
