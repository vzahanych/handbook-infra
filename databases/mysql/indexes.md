# MySQL — indexes

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. B-tree and the clustered index](#1-b-tree-and-the-clustered-index)
  * [2. Composite indexes and leftmost prefix](#2-composite-indexes-and-leftmost-prefix)
  * [3. Covering indexes](#3-covering-indexes)
  * [4. Full-text and spatial indexes](#4-full-text-and-spatial-indexes)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

An index lets MySQL find rows without scanning the table, and under InnoDB indexes are B-trees built on top of the clustered primary key. A secondary index stores the indexed columns plus the primary key, so a lookup may need a second step to fetch the full row unless the index already covers every column the query needs.

Composite indexes follow a leftmost-prefix rule, so column order must match how you filter. You confirm with `EXPLAIN` that the planner actually uses the index you expect.

---

## Detailed explanation with examples

### 1. B-tree and the clustered index

- TODO: secondary index → PK → row lookup
- TODO: why the PK choice affects all indexes

### 2. Composite indexes and leftmost prefix

- TODO: column order matches WHERE/ORDER BY
- TODO: when a composite index can/can't be used

### 3. Covering indexes

- TODO: index-only scans
- TODO: adding columns to cover a hot query

### 4. Full-text and spatial indexes

- TODO: `FULLTEXT` search
- TODO: spatial (`SPATIAL`) indexes

### 5. Practical rule

```text
Order composite index columns to match your filters and sorts.
Cover hot queries to avoid extra row lookups; verify with EXPLAIN.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: respect leftmost-prefix; avoid functions on indexed columns in WHERE
- TODO: design covering indexes for read-hot paths

### Operations and production

- TODO: drop unused/redundant indexes; watch index write overhead
- TODO: review slow query log + `EXPLAIN` regularly

## References

- Official docs: https://dev.mysql.com/doc/
- Overview: [fundamentals.md](fundamentals.md)
