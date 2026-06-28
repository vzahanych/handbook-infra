# Redpanda — producers and consumers

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Keyed producers](#1-keyed-producers)
  * [2. Consumer groups and offsets](#2-consumer-groups-and-offsets)
  * [3. Delivery semantics](#3-delivery-semantics)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Producing and consuming in Redpanda follows the Kafka model unchanged: producers append keyed records, the key chooses the partition and preserves per-key ordering, and consumer groups divide partitions for parallel reads while tracking offsets. Acknowledgement settings and idempotence behave as in Kafka, so the same durability-versus-throughput trade-offs apply.

Delivery semantics — at-most-once, at-least-once, exactly-once — carry over identically. The practical guidance is the same as Kafka's, so design clients as you would there.

---

## Detailed explanation with examples

### 1. Keyed producers

- TODO: key → partition → ordering; acks/idempotence

### 2. Consumer groups and offsets

- TODO: group partition assignment; offset commits

### 3. Delivery semantics

- TODO: at-least-once default; idempotent consumers; transactions

### 4. Practical rule

```text
Same as Kafka: key for ordering, acks=all + idempotence, idempotent consumers.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: reuse Kafka client patterns directly

### Operations and production

- TODO: monitor lag; test failure/commit behavior

## References

- Official docs: https://docs.redpanda.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../kafka/offsets-and-delivery-semantics.md](../kafka/offsets-and-delivery-semantics.md)
