###############################################
# STAGE 1 — Build (instala dependências)
###############################################
FROM python:3.12-slim AS builder

# Evitar cache de pip e garantir ambiente limpo
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Instalar dependências de build (somente aqui)
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Copiar requisitos
COPY requirements.txt .

# Instalar dependências em /install (isolado do sistema)
RUN pip install --user --no-cache-dir -r requirements.txt


###############################################
# STAGE 2 — Runtime (imagem final, leve)
###############################################
FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Instalar apenas libs essenciais
RUN apt-get update && apt-get install -y --no-install-recommends \
    libpq5 \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Copiar dependências já instaladas no builder
COPY --from=builder /root/.local /root/.local

# Adicionar executáveis locais ao PATH
ENV PATH=/root/.local/bin:$PATH

# Copiar o código da aplicação
COPY . .

# Porta padrão (edite conforme sua app)
EXPOSE 8003

# Comando inicial (altere para sua app)
CMD ["python3", "app.py"]
