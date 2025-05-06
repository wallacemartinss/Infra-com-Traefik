

Para Obter a Key do Chatwoot execute:

```bash
docker exec -it rails bundle exec rails secret 
```

Isso imprimirá no terminal uma chave como:

```bash
3ad45296452d56050430d92c87927205ac90bc378caf840b653f82642b55f07a75014466f099b65cb0460777aba31dbfd9a6aae50225675bbf01261952f5c50b
```

Basta copiar e colar no .env da sua instalação como:

```bash
SECRET_KEY_BASE=3ad45296... (restante da chave)
```

---

Para rodar as migrations no banco de dados do Chatwoot (em produção com Docker), use o comando abaixo dentro do container rails

```bash
docker exec -it rails bundle exec rails db:migrate RAILS_ENV=production
```

💡 Certifique-se de que o banco esteja acessível (PostgreSQL no container postgres) e que as variáveis .env estejam corretamente configuradas.

