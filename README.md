# NestJS Microservices with RabbitMQ / Grafana

Fully managed Microservices starter pack using **NestJS / RabbitMQ**. created with SQL, NoSQL databases, Kong API Gateway, Grafana Logging stack.

## Dependencies & Services

- RabbitMQ - https://www.rabbitmq.com
- Redis - https://redis.io
- Grafana - https://grafana.com
- MognoDB - https://www.mongodb.com
- PostgreSQL - https://www.postgresql.org
- Kong - https://konghq.com
- Loki - https://grafana.com/oss/loki
- Helm - https://helm.sh
- Fluent-Bit - https://grafana.com/docs/loki/latest/clients/fluentbit

## Get started Notes:

- Use `git submodule update --remote --init` command to update/fetch submodules.
- `kong.yml` from `kong/conf/kong.yml` file is configured for api gateway.
- Kong development server endpoint will start on port `8000`.
- Health endpoint: `host:port/api/health`

## Run in local

start core services first (postgres, rabbitmq, mongodb, redis)

```bash
docker-compose -f docker-compose.dev.yml up
```

Now, first place `.env` file in service folder
then go to service folder `cd auth`

```bash
yarn start:dev
```

#### Run all services in Local Env using docker-compose

```bash
docker-compose up
```

## Setup Grafana Dashboard in Local Env

To see the logs on Grafana dashboard, follow below steps.

1. Open the browser and go to http://localhost:3000, use default credentials username "admin" and password "admin" to login.
2. Now, go to http://localhost:3000/datasources and select Loki from Logging and document databases section.
3. Enter http://loki:3100 in URL under HTTP section. We can do this because we are running Loki and Grafana in the same network.
4. loki else you have to enter host IP address and port here, click on Save and Test button from the bottom of the page.
5. Now, go to 3rd tab "Explore" from the left sidebar or http://localhost:3000/explore
6. select containers and run the query. you will see below view on your screen.
