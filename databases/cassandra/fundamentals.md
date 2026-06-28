# Cassandra — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Keyspaces and the ring](#1-keyspaces-and-the-ring)
  * [2. Tables and the primary key](#2-tables-and-the-primary-key)
  * [3. Partition and clustering keys](#3-partition-and-clustering-keys)
  * [4. Indexes and materialized views](#4-indexes-and-materialized-views)
  * [5. Replication and consistency](#5-replication-and-consistency)
  * [6. Writes and LSM storage](#6-writes-and-lsm-storage)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Cassandra is a masterless, wide-column distributed database. Tables live in a keyspace, and each row is placed on nodes by hashing its partition key, so there is no single master and writes scale horizontally. It speaks CQL, which looks like SQL but is far more restricted.

Modeling in Cassandra is query-first: you design a separate table for each read you need, because there are no joins and you can only query efficiently by the partition key. Relational habits work directly against this — ad-hoc queries, secondary indexes leaned on for filtering, and partitions left to grow without bound all collide with how Cassandra physically stores and reads data. You denormalize on purpose, accepting duplicated data as the price of fast, predictable reads.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Keyspaces and the ring

How tables are grouped, how the token ring distributes partitions, and where the replication strategy is set. See [keyspaces-and-the-ring.md](keyspaces-and-the-ring.md).

### 2. Tables and the primary key

Defining tables in CQL, the data types, and how the primary key both identifies and places a row. See [tables-and-the-primary-key.md](tables-and-the-primary-key.md).

### 3. Partition and clustering keys

How the partition key distributes data while clustering columns order it, and how to keep partitions bounded. See [partition-and-clustering-keys.md](partition-and-clustering-keys.md).

### 4. Indexes and materialized views

Why secondary indexes and materialized views are the exception, and why query tables are the default. See [indexes-and-materialized-views.md](indexes-and-materialized-views.md).

### 5. Replication and consistency

Replication strategy and factor, tunable consistency levels, and how repair keeps replicas in sync. See [replication-and-consistency.md](replication-and-consistency.md).

### 6. Writes and LSM storage

The commit-log → memtable → SSTable write path, compaction strategies, and tombstones. See [writes-and-lsm-storage.md](writes-and-lsm-storage.md).

### 7. Practical rule

```text
Model one table per query; partition key first.
Keep partitions bounded; avoid secondary indexes for scale.
Pick consistency per operation (QUORUM read + QUORUM write = strong).
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: design tables from queries; denormalize freely
- TODO: choose partition keys that bound size and spread load
- TODO: avoid secondary indexes and `ALLOW FILTERING` at scale

### Operations and production

- TODO: `NetworkTopologyStrategy` with RF per datacenter; size quorums
- TODO: choose a compaction strategy per workload; watch tombstones
- TODO: run repairs on schedule; monitor pending compactions and latency

## References

- Official docs: https://cassandra.apache.org/doc/
- Related: [scylladb/fundamentals.md](../scylladb/fundamentals.md)
