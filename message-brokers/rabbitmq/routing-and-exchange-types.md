# RabbitMQ — routing and exchange types

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Direct and fanout](#1-direct-and-fanout)
  * [2. Topic and headers](#2-topic-and-headers)
  * [3. Routing keys and patterns](#3-routing-keys-and-patterns)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

How an exchange routes depends on its type, and choosing the type is the core of RabbitMQ design. A direct exchange routes by exact routing-key match, good for point-to-point work queues; a topic exchange matches routing keys against wildcard patterns, good for category-based pub/sub; a fanout exchange ignores the key and copies to every bound queue, good for broadcast; and a headers exchange routes on message attributes.

The routing key and binding pattern together express the topology, so most messaging behavior is configured here rather than coded.

---

## Detailed explanation with examples

### 1. Direct and fanout

- TODO: direct (exact key) for work queues; fanout for broadcast

### 2. Topic and headers

- TODO: topic wildcard patterns (`*`, `#`); headers on attributes

### 3. Routing keys and patterns

- TODO: routing key conventions; binding patterns

### 4. Practical rule

```text
direct = point-to-point, topic = category pub/sub, fanout = broadcast.
Express behavior in routing keys + bindings, not producer code.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pick the simplest exchange type that fits; design clear routing-key schemes

### Operations and production

- TODO: document routing topology; avoid overly complex header routing

## References

- Official docs: https://www.rabbitmq.com/documentation.html
- Overview: [fundamentals.md](fundamentals.md)
