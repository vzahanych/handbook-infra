# ActiveMQ Artemis — addresses, queues, and routing

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Addresses and queues](#1-addresses-and-queues)
  * [2. Anycast and multicast](#2-anycast-and-multicast)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Artemis centers on addresses, queues, and routing types, which is a slightly different model from older brokers. A producer sends a message to a named address, and the address's routing type determines delivery: anycast routes each message to a single queue's consumer, giving point-to-point semantics, while multicast copies the message to a queue per subscriber, giving publish-subscribe.

Queues are bound to addresses, and one address can host multiple queues. Thinking in addresses and routing types is the key to configuring both work queues and topics in one consistent way.

---

## Detailed explanation with examples

### 1. Addresses and queues

- TODO: producers send to addresses; queues bound to addresses

### 2. Anycast and multicast

- TODO: anycast = point-to-point (queue); multicast = pub-sub (topic)

### 3. Practical rule

```text
Send to addresses; choose anycast for work queues, multicast for topics.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pick routing type per address by point-to-point vs fan-out need

### Operations and production

- TODO: manage address/queue config and auto-create policies deliberately

## References

- Official docs: https://activemq.apache.org/components/artemis/documentation/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [producers-and-consumers.md](producers-and-consumers.md)
