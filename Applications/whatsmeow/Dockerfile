# Etapa 1: build do Whatsmeow
FROM golang:1.22-alpine AS builder

WORKDIR /build

RUN apk add --no-cache git

# Clona o repositório oficial
RUN git clone https://github.com/tulir/whatsmeow.git

WORKDIR /build/whatsmeow

# Instala dependências e compila o exemplo
RUN go mod tidy && go build -o /build/whatsmeow-bin ./cmd/example

# Etapa 2: imagem final enxuta
FROM alpine:latest

WORKDIR /app

RUN apk add --no-cache ca-certificates

# Copia o binário compilado
COPY --from=builder /build/whatsmeow-bin /app/whatsmeow

# Cria diretório para persistência de sessão
RUN mkdir -p /app/storage

VOLUME ["/app/storage"]

CMD ["./whatsmeow"]
