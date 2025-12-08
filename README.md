# Configuração dos `.env` para cada micro-serviço

Abaixo estão todos os arquivos `.env` necessários.  
Basta copiar cada seção para o respectivo serviço na pasta correta e preencher corretamente as AWS keys e intenal SERVICE_API_KEY (ou MASTER_KEY) baseando-se no README.md de cada microservice.

---

```env
## analytics-service
PORT=8005
AWS_SQS_URL=
AWS_DYNAMODB_TABLE=ToggleMasterAnalytics
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_SESSION_TOKEN=


## auth-service
PORT=8001
DATABASE_URL=postgres://postgres:postgres@postgres_auth:5432/auth_service?sslmode=disable
MASTER_KEY=admin-secreto-123
SERVICE_NAME=auth_service


## evaluation-service
PORT=8004
REDIS_URL=redis://redis:6379
FLAG_SERVICE_URL=http://flag_service:8002
TARGETING_SERVICE_URL=http://targeting_service:8003
SERVICE_API_KEY=

AWS_SQS_URL=
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_SESSION_TOKEN=


## flag-service
PORT=8002
DATABASE_URL=postgres://postgres:postgres@postgres_flag:5432/flag_service?sslmode=disable
AUTH_SERVICE_URL=http://auth_service:8001
MASTER_KEY=


## targeting-service
PORT=8003
DATABASE_URL=postgres://postgres:postgres@postgres_targeting:5432/targeting_service?sslmode=disable
AUTH_SERVICE_URL=http://auth_service:8001
MASTER_KEY=admin-secreto-123
```

---
