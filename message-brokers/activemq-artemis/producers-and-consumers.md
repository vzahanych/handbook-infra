# ActiveMQ Artemis — producers and consumers

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Sending and acknowledging](#1-sending-and-acknowledging)
  * [2. Redelivery and dead-letter](#2-redelivery-and-dead-letter)
  * [3. Priorities and message grouping](#3-priorities-and-message-grouping)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Producers send messages to an address and consumers receive them from queues bound to that address, with the routing type deciding whether delivery is point-to-point or fan-out. Reliability rests on acknowledgement: a consumer acknowledges a message after processing, and unacknowledged messages are redelivered, giving at-least-once delivery.

Messages can carry priorities, expirations, and be grouped so related messages go to the same consumer in order. Designing acknowledgement and grouping correctly is what makes consumption reliable and ordered where it matters.

---

## Detailed explanation with examples

### 1. Sending and acknowledging

- TODO: send to address; ack after processing; at-least-once

### 2. Redelivery and dead-letter

- TODO: redelivery on failure; dead-letter address; redelivery delay

### 3. Priorities and message grouping

- TODO: priorities, expiry; message grouping for per-key ordering

### 4. Practical rule

```text
Ack after success; rely on redelivery + dead-letter for failures.
Use message grouping when related messages must stay ordered on one consumer.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: idempotent consumers; configure dead-letter and redelivery policies

### Operations and production

- TODO: monitor delivering/dead-letter counts; tune redelivery limits

## References

- Official docs: https://activemq.apache.org/components/artemis/documentation/
- Overview: [fundamentals.md](fundamentals.md)
