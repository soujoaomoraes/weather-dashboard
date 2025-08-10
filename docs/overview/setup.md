# Guia de Configuração do Ambiente de Desenvolvimento

Este guia descreve os passos necessários para configurar e executar o ambiente de desenvolvimento local do Weather Dashboard.

## Pré-requisitos

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## 1. Configuração do Ambiente

O projeto utiliza arquivos `.env` para gerenciar as variáveis de ambiente. Você precisará criar dois arquivos: um na raiz do projeto para o banco de dados e outro dentro do diretório `backend`.

### 1.1. Variáveis do Banco de Dados

Crie um arquivo chamado `.env` na raiz do projeto (`/home/joaomoraes/projetos/weather-dashboard/.env`) com o seguinte conteúdo:

```env
# Variáveis para o serviço do Postgres no docker-compose.yml
DB_USERNAME=admin
DB_PASSWORD=admin
DB_DATABASE=weather_dashboard
```

### 1.2. Variáveis do Backend

Crie um arquivo chamado `.env` dentro do diretório `backend` (`/home/joaomoraes/projetos/weather-dashboard/backend/.env`) com o seguinte conteúdo:

```env
# URL de conexão com o banco de dados
# O host 'db' é o nome do serviço do Postgres no docker-compose.yml
DATABASE_URL="postgresql://admin:admin@db:5432/weather_dashboard?schema=public"

# Configurações do Redis
# O host 'redis' é o nome do serviço do Redis no docker-compose.yml
REDIS_HOST=redis
REDIS_PORT=6379

# Porta da aplicação backend
PORT=3000
```
*Nota: Estas são as variáveis de ambiente padrão que a aplicação backend deve utilizar para se conectar aos outros serviços.*

## 2. Executando a Aplicação

Com os arquivos `.env` criados, você pode construir e iniciar os contêineres.

```bash
# Constrói as imagens, caso ainda não tenham sido construídas
docker-compose build

# Inicia todos os serviços em modo detached
docker-compose up -d
```

## 3. Acessando os Serviços

Após a inicialização, os serviços estarão disponíveis nos seguintes endereços:

- **Frontend:** [http://localhost](http://localhost) (Porta 80 do host mapeada para a 3000 do contêiner)
- **Backend:** [http://localhost:3001](http://localhost:3001) (Porta 3001 do host mapeada para a 3000 do contêiner)
- **Banco de Dados (Postgres):** Porta `5432` no host
- **Cache (Redis):** Porta `6379` no host

## 4. Parando a Aplicação

Para parar todos os serviços, execute:

```bash
docker-compose down
```
