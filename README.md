# 🔧 Toggle Master — Plataforma de Feature Flags (Microservices Architecture)

Este projeto representa uma arquitetura distribuída composta por cinco micro-serviços, cada um responsável por uma parte essencial do sistema de feature flags, autenticação, avaliação, segmentação e analytics.

Todos os serviços possuem `.env` individuais e dependem de componentes como PostgreSQL, Redis, AWS SQS e DynamoDB.

------------------------------------------------------------
📁 ESTRUTURA DOS MICRO-SERVIÇOS
------------------------------------------------------------

/auth-service  
/evaluation-service  
/flag-service  
/targeting-service  
/analytics-service  

Cada serviço possui responsabilidade isolada e um banco de dados próprio.

------------------------------------------------------------
📦 CONFIGURAÇÃO DE AMBIENTE (.env)
------------------------------------------------------------

Crie um arquivo `.env` na raiz de cada micro-serviço usando as variáveis abaixo.

------------------------------------------------------------
🔍 analytics-service — .env
------------------------------------------------------------

PORT=8005
AWS_SQS_URL=
AWS_DYNAMODB_TABLE=ToggleMasterAnalytics
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_SESSION_TOKEN=

------------------------------------------------------------
🔐 auth-service — .env
------------------------------------------------------------

PORT=8001
DATABASE_URL=postgres://postgres:postgres@postgres_auth:5432/auth_service?sslmode=disable
MASTER_KEY=admin-secreto-123
SERVICE_NAME=auth_service

------------------------------------------------------------
🧠 evaluation-service — .env
------------------------------------------------------------

PORT=8004
REDIS_URL=redis://redis:6379
FLAG_SERVICE_URL=http://flag_service:8002
TARGETING_SERVICE_URL=http://targeting_service:8003
SERVICE_API_KEY=tm_key_086ebd8caaf833cb6f0a03d47eeec5735ef2e9bce35ce6808f159296ca83dad0
AWS_SQS_URL=https://sqs.us-east-1.amazonaws.com/728391875410/myEvaluationQueue
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_SESSION_TOKEN=

------------------------------------------------------------
🚩 flag-service — .env
------------------------------------------------------------

PORT=8002
DATABASE_URL=postgres://postgres:postgres@postgres_flag:5432/flag_service?sslmode=disable
AUTH_SERVICE_URL=http://auth_service:8001
MASTER_KEY=tm_key_1fab542c112f8b92387c9624325daea915614470c89e0feb396c9a83e267d588

------------------------------------------------------------
🎯 targeting-service — .env
------------------------------------------------------------

PORT=8003
DATABASE_URL=postgres://postgres:postgres@postgres_targeting:5432/targeting_service?sslmode=disable
AUTH_SERVICE_URL=http://auth_service:8001
MASTER_KEY=admin-secreto-123

------------------------------------------------------------
🚀 SUBINDO TODOS OS SERVIÇOS (DOCKER)
------------------------------------------------------------

docker-compose up --build -d

Logs:
docker-compose logs -f <service>

------------------------------------------------------------
🧪 DOCUMENTAÇÃO
------------------------------------------------------------

Cada serviço possui sua própria pasta de documentação:

/auth-service/docs  
/evaluation-service/docs  
/flag-service/docs  
/targeting-service/docs  
/analytics-service/docs  

------------------------------------------------------------
🛑 SEGURANÇA IMPORTANTE
------------------------------------------------------------

Nunca envie `.env` para o GitHub.

Use o .gitignore:

.env
*.env
**/*.env

Caso alguma AWS Key tenha sido exposta, gere novas imediatamente.

------------------------------------------------------------
📄 LICENÇA
------------------------------------------------------------

Projeto de uso acadêmico/educacional para estudo de micro-serviços.

