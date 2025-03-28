FROM traefik:latest

# Cria o diretório e define as permissões corretas
RUN mkdir -p /certs && \
    touch /certs/acme.json && \
    chmod 600 /certs/acme.json

# Define o usuário Traefik (Opcional, mas recomendado para segurança)
USER root

CMD ["traefik"]