# ScyllaDB — indexes and materialized views

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Global versus local secondary indexes](#1-global-versus-local-secondary-indexes)
  * [2. Materialized views](#2-materialized-views)
  * [3. Query tables as the default](#3-query-tables-as-the-default)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

ScyllaDB offers the same query-by-other-columns mechanisms as Cassandra — secondary indexes and materialized views — and the same caution applies. Scylla distinguishes global secondary indexes, backed by a hidden materialized view and queryable clusterwide, from local secondary indexes that share the base table's partitioning.

Materialized views maintain a second copy of the data under a new key, at the cost of extra writes. As with Cassandra, the most predictable approach for important access paths remains a denormalized query table you maintain yourself.

---

## Detailed explanation with examples

### 1. Global versus local secondary indexes

- TODO: global (MV-backed) vs local indexes
- TODO: query cost differences

### 2. Materialized views

- TODO: `CREATE MATERIALIZED VIEW`; write amplification

### 3. Query tables as the default

- TODO: denormalized tables per query

### 4. Practical rule

```text
Prefer query tables; use global indexes/MVs only when they clearly fit.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: default to denormalized query tables; avoid high-cardinality local indexes

### Operations and production

- TODO: budget write throughput for MVs/indexes; monitor their consistency

## References

- Official docs: https://docs.scylladb.com/
- Overview: [fundamentals.md](fundamentals.md)
