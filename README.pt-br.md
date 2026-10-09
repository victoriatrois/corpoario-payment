# corpoario-payment

Microsserviço de **Pagamentos** da plataforma de ateliê digital. Java 25, Maven e Quarkus 3.33 (BOM `io.quarkus.platform:quarkus-bom`).

Esta é apenas a estrutura inicial: não há endpoints, entidades, mensageria nem integração com o provedor de pagamento.

## Stack

REST + Jackson, Hibernate ORM com Panache, PostgreSQL, Flyway, Hibernate Validator, REST Client, RabbitMQ (SmallRye Reactive Messaging), SmallRye Fault Tolerance, OpenAPI/Swagger UI, Health e Micrometer/Prometheus.

## Pré-requisitos

JDK 25 e Maven 3.9+. PostgreSQL e RabbitMQ são necessários ao executar (em modo dev o Quarkus pode subir containers via Dev Services, se houver Docker).

## Executar

```sh
mvn quarkus:dev      # modo desenvolvimento
mvn package          # build
java -jar target/quarkus-app/quarkus-run.jar
```

Endpoints de infraestrutura: `/q/health`, `/q/metrics`, `/q/openapi`, `/q/swagger-ui`.

Migrações Flyway ficam em `src/main/resources/db/migration` (`V1__descricao.sql`).

## Configuração (variáveis de ambiente)

| Variável | Padrão |
|---|---|
| `DB_URL` | `jdbc:postgresql://localhost:5432/payment` |
| `DB_USER` / `DB_PASSWORD` | `payment` / `payment` (apenas desenvolvimento local) |
| `RABBITMQ_HOST` / `RABBITMQ_PORT` | `localhost` / `5672` |
| `RABBITMQ_USER` / `RABBITMQ_PASSWORD` | `guest` / `guest` (apenas desenvolvimento local) |
| `PAYMENT_PROVIDER_BASE_URL` | vazio |
| `PAYMENT_PROVIDER_API_KEY` | vazio (nunca versionar) |
