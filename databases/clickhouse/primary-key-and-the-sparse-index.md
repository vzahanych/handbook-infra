# ClickHouse — primary key and the sparse index

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The sorting key and granules](#1-the-sorting-key-and-granules)
  * [2. Not unique, not for point lookups](#2-not-unique-not-for-point-lookups)
  * [3. Ordering columns for pruning](#3-ordering-columns-for-pruning)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

What ClickHouse calls the primary key is not a uniqueness constraint but a sparse index built from the table's sorting key. Instead of indexing every row, it stores one entry per block of rows (a granule), recording the key value at each block boundary, so a query can skip whole blocks that cannot match and then scan only the survivors.

This makes the order of columns in the sorting key the most important tuning decision: filters on the leading columns prune the most data. Because it is sparse and non-unique, it does not give fast single-row point lookups the way a B-tree primary key would.

---

## Detailed explanation with examples

### 1. The sorting key and granules

- TODO: one index entry per granule; block skipping

### 2. Not unique, not for point lookups

- TODO: PK does not enforce uniqueness
- TODO: poor for single-row lookups

### 3. Ordering columns for pruning

- TODO: low-to-high cardinality ordering; match filters

### 4. Practical rule

```text
Order ORDER BY columns by how you filter (leading = most-pruning).
Do not expect unique-key or point-lookup behavior.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: design the sorting key around real WHERE clauses

### Operations and production

- TODO: tune `index_granularity` only with evidence

## References

- Official docs: https://clickhouse.com/docs
- Overview: [fundamentals.md](fundamentals.md)
