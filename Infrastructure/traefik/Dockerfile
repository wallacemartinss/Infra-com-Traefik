FROM traefik:latest

# Cria o diretório e define as permissões corretas
RUN mkdir -p /letsencrypt && \
    touch /letsencrypt/acme.json && \
    chmod 600 /letsencrypt/acme.json

# Define o usuário Traefik (Opcional, mas recomendado para segurança)
USER root

CMD ["traefik"]