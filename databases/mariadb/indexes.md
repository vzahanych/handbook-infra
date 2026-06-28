# MariaDB — indexes

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. B-tree and composite indexes](#1-b-tree-and-composite-indexes)
  * [2. Covering indexes](#2-covering-indexes)
  * [3. Full-text and spatial indexes](#3-full-text-and-spatial-indexes)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Indexing in MariaDB follows the MySQL model: B-tree indexes over the clustered primary key, composite indexes governed by the leftmost-prefix rule, and covering indexes that satisfy a query from the index alone. Full-text and spatial indexes are available for their specialized cases.

As always, `EXPLAIN` (and MariaDB's `ANALYZE` for actual execution) tells you whether the planner uses the index you intended.

---

## Detailed explanation with examples

### 1. B-tree and composite indexes

- TODO: leftmost-prefix rule; column order

### 2. Covering indexes

- TODO: index-only scans for hot queries

### 3. Full-text and spatial indexes

- TODO: `FULLTEXT`, `SPATIAL` use cases

### 4. Practical rule

```text
Order composite columns to your filters/sorts; cover hot reads.
Verify with EXPLAIN / ANALYZE.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: respect leftmost-prefix; avoid functions on indexed columns in WHERE

### Operations and production

- TODO: drop unused indexes; monitor slow queries

## References

- Official docs: https://mariadb.com/kb/en/documentation/
- Overview: [fundamentals.md](fundamentals.md)
