# RabbitMQ — producers and consumers

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Publishing messages](#1-publishing-messages)
  * [2. Acknowledgements](#2-acknowledgements)
  * [3. Prefetch and fair dispatch](#3-prefetch-and-fair-dispatch)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

A producer publishes a message with a routing key to an exchange, and a consumer subscribes to a queue and processes messages from it. The critical detail on the consumer side is acknowledgement: with manual acks, a message is redelivered if the consumer dies before acking, giving at-least-once delivery; with auto-ack, a crash loses it.

A prefetch setting limits how many unacknowledged messages a consumer holds, which is how you balance load fairly across consumers. Designing consumers to ack only after successful processing, and to be idempotent, is what makes delivery reliable.

---

## Detailed explanation with examples

### 1. Publishing messages

- TODO: publish with routing key; message properties

### 2. Acknowledgements

- TODO: manual ack (at-least-once) vs auto-ack (lossy)
- TODO: nack/reject and requeue

### 3. Prefetch and fair dispatch

- TODO: `prefetch_count` (QoS); fair work distribution

### 4. Practical rule

```text
Use manual acks; ack only after successful processing; keep consumers idempotent.
Set prefetch to balance load and bound in-flight work.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: manual ack after success; idempotent handlers; tune prefetch

### Operations and production

- TODO: monitor unacked messages and redelivery rates

## References

- Official docs: https://www.rabbitmq.com/documentation.html
- Overview: [fundamentals.md](fundamentals.md)
- Related: [delivery-guarantees-and-durability.md](delivery-guarantees-and-durability.md)
