# Setup Arcanimal
Para rodar a aplicação localmente é necessário utilizar o seguinte tutorial


## Requisitos
    Caso não saiba como instalar considere ler os links referenciados.

-   [docker](https://docs.docker.com/engine/install/)
-   [git](https://git-scm.com/downloads)

## Processo

### Clone os repositórios
    PS - Caso não saiba como clonar um repositório considere abrir a seguinte referência: https://docs.github.com/pt/repositories/creating-and-managing-repositories/cloning-a-repository

  - [API](https://github.com/Arcanimal/arcanimal-api)
  - [Front](https://github.com/Arcanimal/arcanimal-api)

A estrutura das pastas após clonar deve ser a seguinte:

```
.
├── arcanimal-api
└── arcanimal-front
```

### Atualize seu arquivo `arcanimal-api/.venv`
```
JWT_SECRET="teste"
POSTGRES_USER='admin'
POSTGRES_PASSWORD='admin'
POSTGRES_DB='postgres'
DATABASE_URL="postgres://${POSTGRES_USER}:${POSTGRES_PASSWORD}@db:5432/${POSTGRES_DB}"
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=your-email@example.com
SMTP_PASS=your-password
JWT_EXPIRE=30d
API_URL=http://api.localhost
ENV=development
PORT=8000
```

### Execute os contêineres:

```bash
# setup
docker compose -f arcanimal-api/docker-compose.yml app sh -c "yarn migrate"
docker compose -f arcanimal-api/docker-compose.yml app sh -c "yarn generate"
docker compose -f arcanimal-api/docker-compose.yml app sh -c "yarn seed"

# start containers
docker compose -f arcanimal-api/docker-compose.yml up -d --watch

# stop containers
docker compose -f arcanimal-api/docker-compose.yml down
```

### Acessando serviços
-   [Front](http://front.localhost)
- [API](http://api.localhost/api)