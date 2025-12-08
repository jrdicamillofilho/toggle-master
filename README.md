Criar o .env pra cada micro-service na raiz de cada um:

## analytics-service
PORT=8005

# --- Configuração da AWS ---
# Cole a URL da fila SQS que você criou
AWS_SQS_URL=

# Nome da tabela DynamoDB que você criou
AWS_DYNAMODB_TABLE=ToggleMasterAnalytics

# Região dos seus serviços SQS e DynamoDB
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_SESSION_TOKEN=


## auth-service
PORT=8001

# DB exclusivo do AUTH
DATABASE_URL=postgres://postgres:postgres@postgres_auth:5432/auth_service?sslmode=disable

MASTER_KEY=admin-secreto-123

SERVICE_NAME=auth_service


##evaluation-service
PORT=8004

# URL do seu Redis local
REDIS_URL=redis://redis:6379

# URLs dos outros serviços
FLAG_SERVICE_URL=http://flag_service:8002
TARGETING_SERVICE_URL=http://targeting_service:8003

# Chave de API que você criou no passo 2
SERVICE_API_KEY=tm_key_086ebd8caaf833cb6f0a03d47eeec5735ef2e9bce35ce6808f159296ca83dad0

# --- Configuração da AWS (Obrigatório para o desafio) ---
# Cole a URL da fila SQS que você criou no console da AWS
AWS_SQS_URL=https://sqs.us-east-1.amazonaws.com/728391875410/myEvaluationQueue

# Região da sua fila SQS
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_SESSION_TOKEN=


##flag-service
# Porta do serviço
PORT=8002

# DB exclusivo do FLAG-SERVICE
DATABASE_URL=postgres://postgres:postgres@postgres_flag:5432/flag_service?sslmode=disable

# URL interna para comunicar com o auth
AUTH_SERVICE_URL=http://auth_service:8001

# Mantido exatamente como estava
MASTER_KEY=tm_key_1fab542c112f8b92387c9624325daea915614470c89e0feb396c9a83e267d588


##targeting-service
# Porta do serviço
PORT=8003

# DB exclusivo do TARGETING-SERVICE
DATABASE_URL=postgres://postgres:postgres@postgres_targeting:5432/targeting_service?sslmode=disable

# URL interna para comunicar com o auth
AUTH_SERVICE_URL=http://auth_service:8001

# Mantido exatamente como estava
MASTER_KEY=admin-secreto-123



