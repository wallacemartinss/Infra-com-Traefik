# Usando a imagem oficial do Node.js como base
FROM node:19-alpine

# Definindo o diretório de trabalho
WORKDIR /app

# Copiando os arquivos de dependências para dentro do container
COPY package.json package-lock.json ./

# Instalando as dependências da aplicação
RUN npm install

# Instalando as dependências da aplicação
RUN npm update
# Copiando todo o código fonte para dentro do container
COPY . .

# Expondo a porta onde a API vai rodar
EXPOSE 8080

# Comando para iniciar a aplicação
CMD ["npm", "start"]

