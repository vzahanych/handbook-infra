# Pulsar — producers and subscriptions

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Producers](#1-producers)
  * [2. Subscription types](#2-subscription-types)
  * [3. Acknowledgement](#3-acknowledgement)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Producers publish messages to a topic, and consumers always read through a subscription, a named cursor that tracks position; the subscription type determines the delivery pattern. An exclusive or failover subscription gives ordered, single-consumer processing; a shared subscription load-balances messages across many consumers like a work queue; and a key_shared subscription distributes by message key so each key's messages stay ordered on one consumer.

Because the behavior is chosen per subscription rather than baked into the topic, the same topic can be consumed as a queue by one application and as an ordered stream by another.

---

## Detailed explanation with examples

### 1. Producers

- TODO: publishing; keys; batching

### 2. Subscription types

- TODO: exclusive, failover (ordered); shared (queue); key_shared (ordered per key)

### 3. Acknowledgement

- TODO: individual vs cumulative ack; negative ack; ack timeout

### 4. Practical rule

```text
Pick the subscription type for the pattern you want from the same topic.
key_shared keeps per-key order while sharing load.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: use exclusive/failover for strict order, shared for throughput, key_shared for both

### Operations and production

- TODO: monitor subscription backlog and ack timeouts

## References

- Official docs: https://pulsar.apache.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
