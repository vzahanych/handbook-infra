# Redpanda — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Kafka API compatibility](#1-kafka-api-compatibility)
  * [2. Topics and partitions](#2-topics-and-partitions)
  * [3. Producers and consumers](#3-producers-and-consumers)
  * [4. Raft replication](#4-raft-replication)
  * [5. Differences from Kafka](#5-differences-from-kafka)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Redpanda is a streaming platform that speaks the Kafka API, so existing Kafka clients, tooling, and concepts — topics, partitions, consumer groups, offsets — work against it unchanged. What differs is the implementation: Redpanda is a single C++ binary with no JVM and no ZooKeeper, using a thread-per-core design and built-in Raft for replication, which yields lower and more predictable latency on the same hardware.

Because the data model and protocol match Kafka, almost everything you know about Kafka transfers directly, and these cards lean on the Kafka material for the shared concepts. The Redpanda-specific content is about the engine and the operational differences rather than a new mental model.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Kafka API compatibility

How the Kafka wire protocol makes clients and tooling work unchanged. See [kafka-api-compatibility.md](kafka-api-compatibility.md).

### 2. Topics and partitions

The same topic/partition log model as Kafka, over Raft groups. See [topics-and-partitions.md](topics-and-partitions.md).

### 3. Producers and consumers

Keyed producers and consumer groups, identical to Kafka semantics. See [producers-and-consumers.md](producers-and-consumers.md).

### 4. Raft replication

Per-partition Raft for both data replication and consensus. See [raft-replication.md](raft-replication.md).

### 5. Differences from Kafka

No JVM/ZooKeeper, thread-per-core, single binary, self-tuning. See [differences-from-kafka.md](differences-from-kafka.md).

### 6. Practical rule

```text
Design like Kafka; verify version-specific API coverage.
Lean on Redpanda's simpler ops (one binary, no ZooKeeper).
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: reuse Kafka client design (keys, acks, consumer groups, idempotency)
- TODO: confirm any newer Kafka API feature is supported

### Operations and production

- TODO: RF ≥ 3; monitor lag and under-replicated partitions (Kafka-style)
- TODO: use `rpk` and Redpanda Console; let it self-tune rather than JVM-tuning

## References

- Official docs: https://docs.redpanda.com/
- Related: [../kafka/fundamentals.md](../kafka/fundamentals.md)
