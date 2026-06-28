# Cassandra — replication and consistency

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Replication strategies](#1-replication-strategies)
  * [2. Replication factor](#2-replication-factor)
  * [3. Tunable consistency levels](#3-tunable-consistency-levels)
  * [4. Repair and anti-entropy](#4-repair-and-anti-entropy)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Cassandra keeps multiple copies of every partition, and you control both how many copies exist and how strict each read and write is. The keyspace's replication strategy and replication factor set how many replicas there are and across which datacenters, with NetworkTopologyStrategy the production choice.

On each query you then pick a consistency level — how many replicas must respond — and the relationship between the read and write levels decides your guarantees. When the replicas required for a write plus those required for a read together exceed the replication factor, as with QUORUM on both, a read always sees the latest committed write. Background mechanisms like hinted handoff, read repair, and scheduled repair pull divergent replicas back together over time.

---

## Detailed explanation with examples

### 1. Replication strategies

- TODO: `SimpleStrategy` (dev only) vs `NetworkTopologyStrategy`
- TODO: per-datacenter replica placement
- TODO: snitches and topology awareness

### 2. Replication factor

- TODO: choosing RF (commonly 3 per DC)
- TODO: RF vs number of nodes
- TODO: changing RF and the repair that follows

### 3. Tunable consistency levels

- TODO: `ONE`, `QUORUM`, `LOCAL_QUORUM`, `ALL`, `EACH_QUORUM`
- TODO: the R + W > RF rule for strong consistency
- TODO: latency vs consistency trade-offs

### 4. Repair and anti-entropy

- TODO: hinted handoff
- TODO: read repair
- TODO: scheduled `nodetool repair` / reaper

### 5. Practical rule

```text
NetworkTopologyStrategy, RF 3 per DC as a default.
Use LOCAL_QUORUM reads and writes for strong, low-latency consistency.
Run repairs on a schedule to bound replica divergence.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: pick consistency per operation, not globally
- TODO: prefer `LOCAL_QUORUM` in multi-DC to avoid cross-DC latency

### Operations and production

- TODO: schedule repairs (e.g. Reaper) within gc_grace_seconds
- TODO: size quorums for DC/rack failure tolerance; monitor hints/dropped mutations

## References

- Official docs: https://cassandra.apache.org/doc/
- Overview: [fundamentals.md](fundamentals.md)
