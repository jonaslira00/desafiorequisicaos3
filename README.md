# Arquitetura AWS para Consulta e Armazenamento de Dados

##  Descrição

Este projeto apresenta uma arquitetura serverless na AWS voltada para consulta e recuperação de informações, utilizando armazenamento inteligente com separação entre dados recentes e dados arquivados.


##  Arquitetura da Solução

### Fluxo da aplicação

1. O usuário realiza uma solicitação.
2. O Amazon API Gateway recebe a requisição HTTP.
3. O AWS Lambda processa a solicitação.
4. O Amazon RDS retorna os metadados necessários.
5. O Amazon S3 retorna objetos recentes.
6. Objetos com mais de 90 dias são movidos automaticamente para o S3 Glacier através de uma Lifecycle Policy.
7. Quando necessário, os objetos arquivados são restaurados do Glacier para o S3.

---

##  Serviços AWS Utilizados

### 🔹 Amazon API Gateway
Responsável por receber as requisições do cliente e encaminhá-las para a função Lambda.

### 🔹 AWS Lambda
Executa toda a lógica de processamento da aplicação sem necessidade de gerenciamento de servidores.

### 🔹 Amazon RDS
Armazena os metadados e informações relacionais necessárias para consulta dos objetos.

### 🔹 Amazon S3
Armazena os arquivos recentes e disponíveis para acesso rápido.

### 🔹 Amazon S3 Glacier
Responsável pelo armazenamento de arquivos antigos com baixo custo de armazenamento.

### 🔹 S3 Lifecycle Policy
Automatiza a movimentação dos objetos do S3 para o Glacier após 90 dias.

---

