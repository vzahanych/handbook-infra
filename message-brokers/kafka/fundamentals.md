# Kafka — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Topics and partitions](#1-topics-and-partitions)
  * [2. Producers and keys](#2-producers-and-keys)
  * [3. Consumers and consumer groups](#3-consumers-and-consumer-groups)
  * [4. Offsets and delivery semantics](#4-offsets-and-delivery-semantics)
  * [5. Brokers, replication, and the controller](#5-brokers-replication-and-the-controller)
  * [6. Retention and compaction](#6-retention-and-compaction)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Kafka is a distributed log, not a traditional message queue. Producers append records to named topics, each split into ordered partitions, and consumers read those partitions at their own pace by tracking an offset. Because records stay on disk for a configured retention rather than being deleted on consumption, many independent consumers can read the same data, and any consumer can rewind and replay.

This log-centric design is what makes Kafka a backbone for event streaming: ordering holds within a partition, throughput scales by adding partitions and brokers, and durability comes from replicating each partition across brokers. The consequences to keep in mind are that total ordering exists only per partition, and that the partition count and the record key together decide both parallelism and which events stay together.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Topics and partitions

How topics are split into ordered, replicated partitions, the unit of parallelism. See [topics-and-partitions.md](topics-and-partitions.md).

### 2. Producers and keys

How producers append records and how the key decides the partition and ordering. See [producers-and-keys.md](producers-and-keys.md).

### 3. Consumers and consumer groups

How consumer groups share partitions and scale out reads. See [consumers-and-consumer-groups.md](consumers-and-consumer-groups.md).

### 4. Offsets and delivery semantics

Offset tracking and at-most-once, at-least-once, and exactly-once delivery. See [offsets-and-delivery-semantics.md](offsets-and-delivery-semantics.md).

### 5. Brokers, replication, and the controller

Brokers, partition replication, the ISR, and the controller (KRaft/ZooKeeper). See [brokers-replication-and-the-controller.md](brokers-replication-and-the-controller.md).

### 6. Retention and compaction

Time/size retention versus log compaction for keyed state. See [retention-and-compaction.md](retention-and-compaction.md).

### 7. Practical rule

```text
Partition for parallelism; key for ordering and co-location.
Pick a delivery guarantee deliberately; replicate for durability.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: choose partition count for target parallelism; key by entity for ordering
- TODO: pick acks/idempotence/transactions to match the delivery guarantee
- TODO: design consumers to be idempotent (at-least-once is the common default)

### Operations and production

- TODO: replication factor ≥ 3, `min.insync.replicas` ≥ 2 for durability
- TODO: monitor consumer lag, under-replicated partitions, ISR shrink
- TODO: plan retention/compaction and disk capacity per topic

## References

- Official docs: https://kafka.apache.org/documentation/
- Related: [../redpanda/fundamentals.md](../redpanda/fundamentals.md)
