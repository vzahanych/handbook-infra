# ClickHouse — data skipping indexes and projections

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Data skipping indexes](#1-data-skipping-indexes)
  * [2. Projections](#2-projections)
  * [3. Reading the query pipeline](#3-reading-the-query-pipeline)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Beyond the sparse primary index, ClickHouse offers data skipping indexes and projections to avoid reading blocks that cannot contribute to a query. A skipping index stores a small summary per block — a min/max range, a set of values, or a bloom filter — letting the engine discard blocks whose summary rules out a match.

Projections go further by maintaining an alternative physical ordering or pre-aggregation of the same table, so a query that does not align with the main sort order can still be served efficiently. Both are optimizations layered on top of the sorting key, not replacements for choosing it well.

---

## Detailed explanation with examples

### 1. Data skipping indexes

- TODO: `minmax`, `set`, `bloom_filter` index types
- TODO: when each helps

### 2. Projections

- TODO: alternative ordering / pre-aggregation of the same table

### 3. Reading the query pipeline

- TODO: `EXPLAIN`; rows read vs rows in table

### 4. Practical rule

```text
Fix the sorting key first; add skipping indexes/projections for off-axis queries.
Verify they reduce rows read with EXPLAIN.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: add skipping indexes for selective off-key filters; projections for alternate sorts

### Operations and production

- TODO: measure read-row reduction before/after; mind extra storage from projections

## References

- Official docs: https://clickhouse.com/docs
- Overview: [fundamentals.md](fundamentals.md)
