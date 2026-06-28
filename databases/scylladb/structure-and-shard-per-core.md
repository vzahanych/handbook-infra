# ScyllaDB — structure and shard-per-core

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Cassandra-compatible structure](#1-cassandra-compatible-structure)
  * [2. The shard-per-core engine](#2-the-shard-per-core-engine)
  * [3. Shard-aware drivers](#3-shard-aware-drivers)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

ScyllaDB keeps Cassandra's structure — clusters of keyspaces and tables, distributed by hashing the partition key around a token ring — so at the data-model level it is the same database. What changes is the engine: ScyllaDB is written in C++ and uses a shard-per-core architecture, where each CPU core owns a slice of the data and runs its own event loop with no shared state.

Because a partition is pinned not just to a node but to a specific core, shard-aware drivers can send a request straight to the core that owns the data, avoiding cross-core hops. This is why Scylla reaches higher throughput and lower latency on the same hardware without changing how you model.

---

## Detailed explanation with examples

### 1. Cassandra-compatible structure

- TODO: cluster → keyspace → table; CQL parity

### 2. The shard-per-core engine

- TODO: thread-per-core, shared-nothing design
- TODO: partitions pinned to a core

### 3. Shard-aware drivers

- TODO: routing requests to the owning shard

### 4. Practical rule

```text
Model exactly like Cassandra; use shard-aware drivers for full throughput.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: same modeling rules as Cassandra apply

### Operations and production

- TODO: use shard-aware drivers; size cores/RAM per Scylla guidance

## References

- Official docs: https://docs.scylladb.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../cassandra/fundamentals.md](../cassandra/fundamentals.md)
