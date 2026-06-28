# RabbitMQ — exchanges, queues, and bindings

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Publish to an exchange](#1-publish-to-an-exchange)
  * [2. Queues hold messages](#2-queues-hold-messages)
  * [3. Bindings connect them](#3-bindings-connect-them)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

The three building blocks of RabbitMQ are exchanges, queues, and the bindings that connect them. A producer never publishes directly to a queue; it publishes to an exchange, which uses the message's routing key and the bindings to decide which queues receive a copy.

A queue holds messages until a consumer takes them, and a binding is the rule linking an exchange to a queue, optionally with a pattern. This separation lets you change routing topology — add a consumer queue, fan a message out, reroute by pattern — without touching producers.

---

## Detailed explanation with examples

### 1. Publish to an exchange

- TODO: producers publish to exchanges with a routing key

### 2. Queues hold messages

- TODO: queues store until consumed/acked; deleted on ack

### 3. Bindings connect them

- TODO: binding = exchange → queue rule, with optional pattern

### 4. Practical rule

```text
Never couple producers to queues; publish to exchanges and route via bindings.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: keep producers ignorant of consumers; evolve topology via bindings

### Operations and production

- TODO: declare durable exchanges/queues; manage topology as code

## References

- Official docs: https://www.rabbitmq.com/documentation.html
- Overview: [fundamentals.md](fundamentals.md)
- Related: [routing-and-exchange-types.md](routing-and-exchange-types.md)
