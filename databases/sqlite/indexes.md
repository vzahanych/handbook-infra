# SQLite — indexes

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. B-tree indexes](#1-b-tree-indexes)
  * [2. Partial and expression indexes](#2-partial-and-expression-indexes)
  * [3. Reading the query plan](#3-reading-the-query-plan)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

An index in SQLite is a B-tree that lets the engine find rows without scanning the table, supporting composite, partial, and expression indexes much like larger databases. Because SQLite is embedded and often runs on modest hardware, the right index can be the difference between an instant query and a full scan.

`EXPLAIN QUERY PLAN` shows whether a query uses an index or falls back to a scan. As elsewhere, each index costs something on writes, so you index for the queries that matter.

---

## Detailed explanation with examples

### 1. B-tree indexes

- TODO: single and composite indexes; column order

### 2. Partial and expression indexes

- TODO: partial indexes with `WHERE`
- TODO: expression indexes

### 3. Reading the query plan

- TODO: `EXPLAIN QUERY PLAN`; spotting `SCAN` vs `SEARCH`

### 4. Practical rule

```text
Index the queries that matter; confirm with EXPLAIN QUERY PLAN.
Use partial/expression indexes to target specific lookups.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: composite column order matches WHERE + ORDER BY

### Operations and production

- TODO: run `ANALYZE` so the planner has statistics

## References

- Official docs: https://www.sqlite.org/queryplanner.html
- Overview: [fundamentals.md](fundamentals.md)
