# TimescaleDB — indexes

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Per-chunk indexes](#1-per-chunk-indexes)
  * [2. Time-series index patterns](#2-time-series-index-patterns)
  * [3. Postgres index types apply](#3-postgres-index-types-apply)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Indexing a hypertable uses ordinary PostgreSQL indexes, with one twist: an index is created on each chunk rather than once globally, which keeps per-chunk indexes small and fast. Time-series queries almost always filter and sort by time, so the default time index and composite patterns like `(device_id, time DESC)` are the common shapes.

All the Postgres index types remain available — B-tree for most cases, BRIN for very large append-only data, GIN for `jsonb` — so you choose them exactly as you would in plain Postgres. The mental model is normal Postgres indexing applied per chunk.

---

## Detailed explanation with examples

### 1. Per-chunk indexes

- TODO: indexes created per chunk; kept small

### 2. Time-series index patterns

- TODO: default time index; `(device_id, time DESC)` composites

### 3. Postgres index types apply

- TODO: B-tree, BRIN (huge append-only), GIN (`jsonb`)

### 4. Practical rule

```text
Index time + the columns you filter by (e.g. device_id, time DESC).
Consider BRIN for very large append-only hypertables.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: make time leading/secondary in composite indexes for range scans

### Operations and production

- TODO: watch per-chunk index overhead; drop unused indexes

## References

- Official docs: https://docs.tigerdata.com/
- Overview: [fundamentals.md](fundamentals.md)
