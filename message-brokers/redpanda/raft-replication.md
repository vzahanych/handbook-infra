# Redpanda — Raft replication

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Per-partition Raft groups](#1-per-partition-raft-groups)
  * [2. Replication factor and durability](#2-replication-factor-and-durability)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Where Kafka historically separated data replication from metadata coordination, Redpanda uses Raft consensus uniformly: every partition is its own Raft group, and the same protocol that replicates the data also elects leaders and manages membership. This removes the need for ZooKeeper or a separate KRaft quorum and makes replication and consensus a single, well-understood mechanism.

As in Kafka, you set a replication factor and a majority of replicas must acknowledge a write for it to be durable. The benefit is fewer moving parts and simpler, strong consistency guarantees.

---

## Detailed explanation with examples

### 1. Per-partition Raft groups

- TODO: data + leader election + membership all via Raft
- TODO: no ZooKeeper / separate controller quorum

### 2. Replication factor and durability

- TODO: RF; majority acknowledgement for commit

### 3. Practical rule

```text
RF ≥ 3; a write commits on majority acknowledgement.
One mechanism (Raft) for data and consensus — fewer moving parts.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pair acks with RF for the durability you need

### Operations and production

- TODO: spread replicas across AZs; monitor Raft leadership and under-replication

## References

- Official docs: https://docs.redpanda.com/
- Overview: [fundamentals.md](fundamentals.md)
