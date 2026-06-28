# Redpanda — topics and partitions

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The same log model as Kafka](#1-the-same-log-model-as-kafka)
  * [2. Partitions as Raft groups](#2-partitions-as-raft-groups)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Topics and partitions in Redpanda mean exactly what they do in Kafka: a topic is a named log split into ordered partitions, ordering holds within a partition, and partitions are the unit of parallelism and replication. The partition count still sets maximum consumer parallelism and is chosen for throughput.

What changes underneath is that each partition is a Raft group managed directly by Redpanda rather than relying on a separate coordination service. For modeling purposes, treat partitions exactly as you would in Kafka.

---

## Detailed explanation with examples

### 1. The same log model as Kafka

- TODO: ordered partitions; per-partition ordering; parallelism

### 2. Partitions as Raft groups

- TODO: each partition is its own Raft group

### 3. Practical rule

```text
Model partitions exactly like Kafka; size for peak parallelism.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: rely on per-partition ordering only (as in Kafka)

### Operations and production

- TODO: plan partition counts; Redpanda handles replication via Raft

## References

- Official docs: https://docs.redpanda.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../kafka/topics-and-partitions.md](../kafka/topics-and-partitions.md)
