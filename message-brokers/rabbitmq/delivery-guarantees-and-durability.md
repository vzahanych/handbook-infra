# RabbitMQ — delivery guarantees and durability

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Durable queues and persistent messages](#1-durable-queues-and-persistent-messages)
  * [2. Publisher confirms](#2-publisher-confirms)
  * [3. Dead-letter exchanges](#3-dead-letter-exchanges)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Whether a message survives a broker restart or a crash depends on several settings working together. A queue must be declared durable and a message marked persistent for it to be written to disk, and publisher confirms let the producer know the broker actually stored it. On the consumer side, manual acknowledgements provide at-least-once delivery with redelivery on failure.

Dead-letter exchanges capture messages that are rejected or expire, giving you a place to inspect and retry failures. None of these are on by default in the strongest form, so reliable delivery is something you assemble from durable queues, persistent messages, confirms, and manual acks.

---

## Detailed explanation with examples

### 1. Durable queues and persistent messages

- TODO: durable queue + persistent message → survives restart

### 2. Publisher confirms

- TODO: confirms for broker-stored acknowledgement

### 3. Dead-letter exchanges

- TODO: DLX for rejected/expired/over-length messages; retry patterns

### 4. Practical rule

```text
Reliability = durable queue + persistent message + publisher confirm + manual ack.
Route failures to a dead-letter exchange.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: enable confirms; mark messages persistent; design DLX retry flows

### Operations and production

- TODO: verify durability end-to-end; monitor DLX depth

## References

- Official docs: https://www.rabbitmq.com/documentation.html
- Overview: [fundamentals.md](fundamentals.md)
