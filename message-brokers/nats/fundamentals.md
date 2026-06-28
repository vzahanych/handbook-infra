# NATS — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Subjects and pub-sub](#1-subjects-and-pub-sub)
  * [2. Messaging patterns](#2-messaging-patterns)
  * [3. JetStream persistence](#3-jetstream-persistence)
  * [4. Clustering and scaling](#4-clustering-and-scaling)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

NATS is a lightweight messaging system organized around subjects — dot-delimited names like `orders.eu.created` that publishers send to and subscribers listen on, with wildcards for flexible matching. The core of NATS is fire-and-forget publish-subscribe: messages are delivered to whoever is currently subscribed and are not stored, which makes it extremely fast and simple for real-time signaling and request-reply.

For durability, NATS adds JetStream, a persistence layer that captures messages from subjects into streams that can be replayed, acknowledged, and retained — turning the same system into something closer to a log or queue. The split to keep in mind is core NATS for ephemeral, low-latency messaging and JetStream when you need storage and delivery guarantees.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Subjects and pub-sub

The dot-delimited subject namespace, wildcards, and ephemeral pub-sub. See [subjects-and-pub-sub.md](subjects-and-pub-sub.md).

### 2. Messaging patterns

Publish-subscribe, request-reply, and load-balanced queue groups. See [messaging-patterns.md](messaging-patterns.md).

### 3. JetStream persistence

Streams and consumers for durable, replayable, acknowledged delivery. See [jetstream-persistence.md](jetstream-persistence.md).

### 4. Clustering and scaling

Clusters, superclusters/leaf nodes, and JetStream replication. See [clustering-and-scaling.md](clustering-and-scaling.md).

### 5. Practical rule

```text
Core NATS for fast ephemeral messaging; JetStream when you need durability.
Design a clear subject hierarchy — routing and security build on it.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: design hierarchical subjects; use queue groups for work sharing
- TODO: use JetStream (streams + consumers) when delivery must survive restarts

### Operations and production

- TODO: replicate JetStream streams (R3) for durability/failover
- TODO: monitor slow consumers, stream storage, and consumer ack pending

## References

- Official docs: https://docs.nats.io/
- Related: [../kafka/fundamentals.md](../kafka/fundamentals.md)
