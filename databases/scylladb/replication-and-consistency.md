# ScyllaDB — replication and consistency

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Replication strategy and factor](#1-replication-strategy-and-factor)
  * [2. Tunable consistency levels](#2-tunable-consistency-levels)
  * [3. Repair and anti-entropy](#3-repair-and-anti-entropy)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Replication and consistency in ScyllaDB follow the Cassandra model: the keyspace sets a replication strategy and factor, NetworkTopologyStrategy is the production choice, and each query picks a tunable consistency level. The familiar rule still holds that when read and write consistency together exceed the replication factor, as with LOCAL_QUORUM on both, reads see the latest write.

Background repair, hinted handoff, and read repair reconcile divergent replicas over time. The mental model is identical to Cassandra's, so consistency tuning carries over unchanged.

---

## Detailed explanation with examples

### 1. Replication strategy and factor

- TODO: `NetworkTopologyStrategy`; RF per DC

### 2. Tunable consistency levels

- TODO: `ONE`, `QUORUM`, `LOCAL_QUORUM`, `ALL`
- TODO: R + W > RF rule

### 3. Repair and anti-entropy

- TODO: hinted handoff, read repair, Scylla Manager repair

### 4. Practical rule

```text
NetworkTopologyStrategy, RF 3 per DC; LOCAL_QUORUM reads + writes.
Schedule repairs (Scylla Manager).
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: pick consistency per operation; `LOCAL_QUORUM` in multi-DC

### Operations and production

- TODO: schedule repairs; monitor hints and dropped mutations

## References

- Official docs: https://docs.scylladb.com/
- Overview: [fundamentals.md](fundamentals.md)
