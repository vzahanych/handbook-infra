# Cassandra — indexes and materialized views

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Secondary indexes and their cost](#1-secondary-indexes-and-their-cost)
  * [2. SASI and storage-attached indexes](#2-sasi-and-storage-attached-indexes)
  * [3. Materialized views](#3-materialized-views)
  * [4. Query tables as the default](#4-query-tables-as-the-default)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Cassandra offers secondary indexes and materialized views to query by something other than the partition key, but both come with sharp limits that make them the exception rather than the default. A secondary index is local to each node, so a query that uses one may have to fan out to the whole cluster, which scales badly as nodes are added.

Materialized views maintain a second copy of a table under a different key, but they add write cost and have historically been fragile. The reliable pattern stays the same as the rest of Cassandra modeling: write the data into a second table shaped for the second query, a denormalization you manage yourself rather than ask the database to hide.

---

## Detailed explanation with examples

### 1. Secondary indexes and their cost

- TODO: local (per-node) nature and scatter-gather reads
- TODO: where they are acceptable (low cardinality within a partition)
- TODO: why they hurt at scale

### 2. SASI and storage-attached indexes

- TODO: SASI capabilities and limitations
- TODO: storage-attached indexing (SAI) in newer versions
- TODO: when these change the calculus

### 3. Materialized views

- TODO: `CREATE MATERIALIZED VIEW`
- TODO: write amplification and consistency caveats
- TODO: operational status / maturity warnings

### 4. Query tables as the default

- TODO: hand-built denormalized tables per query
- TODO: keeping them in sync (app writes, batches)
- TODO: trade-off: more writes/storage for predictable reads

### 5. Practical rule

```text
Prefer a second query table over an index or a view.
Use secondary indexes only for low-cardinality, in-partition filters.
Treat materialized views as advanced/optional, not a default.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: default to denormalized query tables
- TODO: avoid secondary indexes on high-cardinality columns
- TODO: evaluate SAI (newer versions) before reaching for SASI

### Operations and production

- TODO: monitor MV consistency and repair behavior if used
- TODO: budget extra write throughput/storage for query tables

## References

- Official docs: https://cassandra.apache.org/doc/
- Overview: [fundamentals.md](fundamentals.md)
