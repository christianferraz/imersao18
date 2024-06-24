# Etapa de construção
FROM golang:1.22.4-alpine3.20 AS builder

# Defina o diretório de trabalho
WORKDIR /app

# Copie os arquivos go.mod e go.sum
COPY go.mod go.sum ./

# Baixe as dependências
RUN go mod download

# Copie o código-fonte da aplicação
COPY . .

# Construa a aplicação
RUN GOOS=linux CGO_ENABLED=0 go build -ldflags="-w -s" -o server cmd/events/main.go

# Etapa final
FROM scratch

# Copie o binário construído da etapa anterior
COPY --from=builder /app/server .

# Comando de inicialização
CMD ["./server"]
