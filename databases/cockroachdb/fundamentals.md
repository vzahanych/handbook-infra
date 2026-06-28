# CockroachDB — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Ranges replicas and distribution](#1-ranges-replicas-and-distribution)
  * [2. Tables and data types](#2-tables-and-data-types)
  * [3. Keys and avoiding hotspots](#3-keys-and-avoiding-hotspots)
  * [4. Indexes](#4-indexes)
  * [5. Transactions and consistency](#5-transactions-and-consistency)
  * [6. Multi region tables](#6-multi-region-tables)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

CockroachDB is a distributed SQL database. It looks and talks like PostgreSQL, but underneath it stores every table as a set of key ranges that are automatically split, replicated, and rebalanced across nodes. You write ordinary SQL and the cluster handles distribution.

Because the primary key also defines a table's storage order, a sequential key funnels every new write onto the same node and creates a hotspot. Spreading writes across the cluster — with random UUIDs or hash-sharded indexes — is what keeps it balanced, so the single-node Postgres habit of an auto-incrementing key works against you here. Note too that the default isolation is already serializable, stronger than stock Postgres.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Ranges replicas and distribution

How SQL maps onto a sorted key-value store of ranges, replicated by Raft. See [ranges-replicas-and-distribution.md](ranges-replicas-and-distribution.md).

### 2. Tables and data types

PostgreSQL-compatible tables and types, and where compatibility stops. See [tables-and-data-types.md](tables-and-data-types.md).

### 3. Keys and avoiding hotspots

Why the primary key sets storage order, and how to spread writes. See [keys-and-avoiding-hotspots.md](keys-and-avoiding-hotspots.md).

### 4. Indexes

Distributed secondary indexes, `STORING` covering reads, inverted/partial indexes. See [indexes.md](indexes.md).

### 5. Transactions and consistency

Serializable-by-default isolation, distributed transactions, and retries. See [transactions-and-consistency.md](transactions-and-consistency.md).

### 6. Multi region tables

Table localities, survival goals, and data residency. See [multi-region-tables.md](multi-region-tables.md).

### 7. Practical rule

```text
Write SQL like Postgres, but choose keys like a distributed system.
Avoid sequential PKs; spread writes; expect transaction retries.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer UUID or hash-sharded PKs to avoid range hotspots
- TODO: design for serializable isolation; implement retry loops
- TODO: use `STORING` to make hot reads index-only

### Operations and production

- TODO: size ranges, watch leaseholder balance and hot ranges
- TODO: backups (`BACKUP`/`RESTORE`), changefeeds
- TODO: configure regions/survival goals for multi-region clusters

## References

- Official docs: https://www.cockroachlabs.com/docs/
- Related: [postgresql/fundamentals.md](../postgresql/fundamentals.md)
