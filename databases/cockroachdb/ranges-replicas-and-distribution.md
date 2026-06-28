# CockroachDB — ranges, replicas, and distribution

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. SQL over a key-value store](#1-sql-over-a-key-value-store)
  * [2. Ranges, replicas, and leaseholders](#2-ranges-replicas-and-leaseholders)
  * [3. Splitting and rebalancing](#3-splitting-and-rebalancing)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Underneath its SQL surface, CockroachDB is a distributed key-value store, and every table and index is encoded into a sorted keyspace that is cut into contiguous chunks called ranges. Each range is replicated to several nodes and kept consistent by the Raft consensus protocol, with one replica acting as the leaseholder that serves reads and coordinates writes.

As ranges grow or traffic shifts, the cluster splits, merges, and rebalances them automatically, so capacity scales by adding nodes rather than resharding by hand. This machinery is invisible in SQL but explains every performance characteristic above it.

---

## Detailed explanation with examples

### 1. SQL over a key-value store

- TODO: how rows/indexes encode into sorted keys
- TODO: the distribution layer beneath SQL

### 2. Ranges, replicas, and leaseholders

- TODO: range = unit of replication
- TODO: Raft consensus; leaseholder serves reads

### 3. Splitting and rebalancing

- TODO: automatic range splits/merges
- TODO: rebalancing across nodes; hot ranges

### 4. Practical rule

```text
Think in ranges: data is sorted, split, and replicated automatically.
Add nodes to scale; do not shard by hand.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: design keys aware that data is stored in sorted ranges

### Operations and production

- TODO: monitor hot ranges and leaseholder balance; watch Raft health

## References

- Official docs: https://www.cockroachlabs.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
