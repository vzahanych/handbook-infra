# ScyllaDB — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Structure and shard per core](#1-structure-and-shard-per-core)
  * [2. Tables and the primary key](#2-tables-and-the-primary-key)
  * [3. Partition and clustering keys](#3-partition-and-clustering-keys)
  * [4. Indexes and materialized views](#4-indexes-and-materialized-views)
  * [5. Replication and consistency](#5-replication-and-consistency)
  * [6. Differences from Cassandra](#6-differences-from-cassandra)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

ScyllaDB is a C++ reimplementation of Cassandra. It keeps the same data model and CQL API — keyspaces, tables, partition keys, clustering columns — so the modeling rules are identical. The difference is the engine: a shard-per-core design with no JVM and no garbage collector, which gives lower and more predictable latency.

Everything you know about Cassandra data modeling carries over unchanged, because the gains come from the engine rather than from a different model — the same query-first tables, partition keys, and clustering columns apply. Where the equivalence stops is in the operational details: some features, defaults, drivers, and timing characteristics differ between the two, so confirm specifics against Scylla's own docs instead of assuming exact Cassandra parity.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Structure and shard per core

Cassandra-compatible structure plus the shard-per-core engine and shard-aware drivers. See [structure-and-shard-per-core.md](structure-and-shard-per-core.md).

### 2. Tables and the primary key

CQL tables and the partition + clustering primary key. See [tables-and-the-primary-key.md](tables-and-the-primary-key.md).

### 3. Partition and clustering keys

How the partition key maps to node and core, and keeping partitions bounded. See [partition-and-clustering-keys.md](partition-and-clustering-keys.md).

### 4. Indexes and materialized views

Global vs local secondary indexes, materialized views, and query tables. See [indexes-and-materialized-views.md](indexes-and-materialized-views.md).

### 5. Replication and consistency

Replication strategy and factor, consistency levels, and repair. See [replication-and-consistency.md](replication-and-consistency.md).

### 6. Differences from Cassandra

No JVM/GC, self-tuning schedulers, and feature/tooling differences. See [differences-from-cassandra.md](differences-from-cassandra.md).

### 7. Practical rule

```text
Model exactly like Cassandra; partition key first, partitions bounded.
Use shard-aware drivers to get the full throughput benefit.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: design one table per query; bound partition size
- TODO: prefer query tables over secondary indexes at scale
- TODO: pick consistency per operation

### Operations and production

- TODO: use shard-aware drivers; let Scylla auto-tune
- TODO: `NetworkTopologyStrategy` with RF per DC; schedule repairs
- TODO: monitor per-shard load, compactions, and latency

## References

- Official docs: https://docs.scylladb.com/
- Related: [cassandra/fundamentals.md](../cassandra/fundamentals.md)
