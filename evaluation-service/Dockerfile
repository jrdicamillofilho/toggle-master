FROM golang:1.23-alpine AS builder

WORKDIR /app

#Copia apenas o go.mod primeiro (go.sum pode não existir)
COPY go.mod ./

# Copia o resto do código (agora o módulo vê os imports reais)
COPY . .

# Gera/atualiza go.sum e baixa dependências
RUN go mod tidy

# Compila
RUN go build -o main .


# Imagem final
FROM golang:1.23-alpine
WORKDIR /app

COPY --from=builder /app/main .


EXPOSE 8004

CMD ["./main"]