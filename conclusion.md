
# Apache ActiveMQ & RabbitMQ
ActiveMQ is the old-timer in the line up, but has recently had a major facelift (Artemis) to handle distributed usecases.

Both Artemis and RabbitMQ are AMQP based, with particular and rather complex usecases, primarily centered around flexibility in routing configuration "after-the-fact". And what they sacrifices in the process is the big scale and even less resilience against system failures (intermittent network errors, hardware crashes, ++).

For these reasons, I am recommending against these two systems to be considered here.

# NATS
NATS is excluded because it doesn't have any persistence, so can't handle clients that are gone and then play catch-up.

# Apache Kafka vs Apache Pulsar
## Executive Summary
If proven track record and market recognition is needed, then we should go with Apache Kafka. Kafka is also marginally easier to install and perhaps (difficult to verify) use less resources at the initial start. Everything else speaks in Pulsar's favor;

Notable Features of Pulsar
  * Both traditional messaging as well as stream processing supported.
  * Easier software upgrades and rescaling.
  * Pulsar Functions, similar to Amazon Lamdba
  * Integration with a lot of systems, incl MQTT.
  * Multi-Tenancy, each Tenant with multiple namespaces
