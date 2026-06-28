# RabbitMQ — clustering and quorum queues

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Clustering basics](#1-clustering-basics)
  * [2. Quorum queues](#2-quorum-queues)
  * [3. Streams](#3-streams)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

RabbitMQ runs as a cluster of nodes that share metadata, but a classic queue traditionally lived on a single node, making it a point of failure. Quorum queues, the modern recommendation for reliability, replicate a queue across nodes using the Raft consensus protocol so it survives node loss with consistent, at-least-once semantics.

Streams are a newer queue type offering a replayable, append-only log for high-throughput fan-out, closer to Kafka's model. Choosing the queue type — quorum for reliable work queues, streams for replay — is the main high-availability decision.

---

## Detailed explanation with examples

### 1. Clustering basics

- TODO: nodes share metadata; classic queues are single-node

### 2. Quorum queues

- TODO: Raft-replicated; consistent at-least-once; default for reliability

### 3. Streams

- TODO: append-only replayable log; high fan-out

### 4. Practical rule

```text
Use quorum queues for reliable work queues; streams when you need replay.
Avoid classic mirrored queues for new designs.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pick quorum vs stream by replay/throughput needs

### Operations and production

- TODO: size quorum membership for failure tolerance; monitor Raft/replication health

## References

- Official docs: https://www.rabbitmq.com/documentation.html
- Overview: [fundamentals.md](fundamentals.md)
