# PostgreSQL — indexes

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. B-tree, the default](#1-b-tree-the-default)
  * [2. Specialized index types](#2-specialized-index-types)
  * [3. Partial, expression, and multicolumn indexes](#3-partial-expression-and-multicolumn-indexes)
  * [4. Confirming index usage](#4-confirming-index-usage)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

An index is a separate data structure that lets PostgreSQL find rows without scanning the whole table, and the default B-tree handles the common cases of equality and range lookups on ordered data. PostgreSQL also ships specialized types — GIN for `jsonb` and full-text, GiST for geometric and range data, BRIN for huge naturally-ordered tables, and Hash for equality — so the index type should match the query and data.

Indexes can be partial, on expressions, or span several columns, which lets you target exactly the queries you run. Because each index adds write cost, you confirm with `EXPLAIN ANALYZE` that one is actually used before keeping it.

---

## Detailed explanation with examples

### 1. B-tree, the default

- TODO: equality and range queries; ordering
- TODO: multicolumn leftmost-prefix behavior

### 2. Specialized index types

- TODO: GIN (`jsonb`, arrays, full-text)
- TODO: GiST (geometric, ranges), BRIN (large ordered), Hash (equality)

### 3. Partial, expression, and multicolumn indexes

- TODO: partial indexes with a `WHERE`
- TODO: expression indexes (`lower(email)`)
- TODO: column order in composite indexes

### 4. Confirming index usage

- TODO: `EXPLAIN ANALYZE`
- TODO: spotting seq scans; `pg_stat_user_indexes`

### 5. Practical rule

```text
Index for the queries you run, not for every column.
Match the index type to the data; verify with EXPLAIN ANALYZE.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: composite index column order matches WHERE + ORDER BY
- TODO: use partial/expression indexes to cover specific queries

### Operations and production

- TODO: drop unused indexes (`pg_stat_user_indexes`)
- TODO: build large indexes `CONCURRENTLY` to avoid locking

## References

- Official docs: https://www.postgresql.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
