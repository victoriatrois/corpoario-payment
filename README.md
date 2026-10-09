# corpoario-payment

**Payments** microservice of the digital atelier platform. Java 25, Maven and Quarkus 3.33 (`io.quarkus.platform:quarkus-bom` BOM).

This is only the initial structure: there are no endpoints, entities, messaging or payment provider integration yet.

Portuguese version: [README.pt-br.md](README.pt-br.md)

## Stack

REST + Jackson, Hibernate ORM with Panache, PostgreSQL, Flyway, Hibernate Validator, REST Client, RabbitMQ (SmallRye Reactive Messaging), SmallRye Fault Tolerance, OpenAPI/Swagger UI, Health and Micrometer/Prometheus.

## Prerequisites

JDK 25 and Maven 3.9+. PostgreSQL and RabbitMQ are required at runtime (in dev mode Quarkus can start containers through Dev Services if Docker is available).

## Running

```sh
mvn quarkus:dev      # dev mode
mvn package          # build
java -jar target/quarkus-app/quarkus-run.jar
```

Infrastructure endpoints: `/q/health`, `/q/metrics`, `/q/openapi`, `/q/swagger-ui`.

Flyway migrations live in `src/main/resources/db/migration` (`V1__description.sql`).

## Configuration (environment variables)

| Variable | Default |
|---|---|
| `DB_URL` | `jdbc:postgresql://localhost:5432/payment` |
| `DB_USER` / `DB_PASSWORD` | `payment` / `payment` (local development only) |
| `RABBITMQ_HOST` / `RABBITMQ_PORT` | `localhost` / `5672` |
| `RABBITMQ_USER` / `RABBITMQ_PASSWORD` | `guest` / `guest` (local development only) |
| `PAYMENT_PROVIDER_BASE_URL` | empty |
| `PAYMENT_PROVIDER_API_KEY` | empty (never commit it) |
