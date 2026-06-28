# RabbitMQ — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Exchanges, queues, and bindings](#1-exchanges-queues-and-bindings)
  * [2. Routing and exchange types](#2-routing-and-exchange-types)
  * [3. Producers and consumers](#3-producers-and-consumers)
  * [4. Delivery guarantees and durability](#4-delivery-guarantees-and-durability)
  * [5. Clustering and quorum queues](#5-clustering-and-quorum-queues)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

RabbitMQ is a traditional message broker built around smart routing rather than a log. Producers publish messages to an exchange, the exchange routes them to queues according to bindings and rules, and consumers take messages off queues, which delete them once acknowledged. This indirection between publisher and queue is what makes RabbitMQ flexible: the same message can fan out to many queues or be routed by topic without the producer knowing the consumers.

Unlike Kafka's replayable log, a RabbitMQ message is normally consumed once and then gone, so the model fits task queues and work distribution more than event replay. Acknowledgements, durability flags, and queue types determine how reliably messages survive, and the AMQP protocol underpins it all.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Exchanges, queues, and bindings

The publish-to-exchange, route-to-queue model and the bindings that connect them. See [exchanges-queues-and-bindings.md](exchanges-queues-and-bindings.md).

### 2. Routing and exchange types

Direct, topic, fanout, and headers exchanges and how routing keys work. See [routing-and-exchange-types.md](routing-and-exchange-types.md).

### 3. Producers and consumers

Publishing, consuming, acknowledgements, and prefetch. See [producers-and-consumers.md](producers-and-consumers.md).

### 4. Delivery guarantees and durability

Durable queues, persistent messages, confirms, acks, and dead-lettering. See [delivery-guarantees-and-durability.md](delivery-guarantees-and-durability.md).

### 5. Clustering and quorum queues

Clustering, quorum queues, and streams for high availability. See [clustering-and-quorum-queues.md](clustering-and-quorum-queues.md).

### 6. Practical rule

```text
Producers publish to exchanges, not queues; routing lives in bindings.
For reliability: durable quorum queues + persistent messages + confirms + manual acks.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: choose the exchange type per routing need; keep producers unaware of queues
- TODO: manual ack after success; make consumers idempotent; set sensible prefetch

### Operations and production

- TODO: prefer quorum queues; enable durability + publisher confirms
- TODO: configure dead-letter exchanges; monitor queue depth and unacked counts

## References

- Official docs: https://www.rabbitmq.com/documentation.html
- Related: [../kafka/fundamentals.md](../kafka/fundamentals.md)
