# Cassandra — tables and the primary key

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Defining a table in CQL](#1-defining-a-table-in-cql)
  * [2. CQL data types and collections](#2-cql-data-types-and-collections)
  * [3. The primary key](#3-the-primary-key)
  * [4. Query-first table design](#4-query-first-table-design)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A Cassandra table looks like a SQL table — named, typed columns — but its primary key carries far more weight, because it both identifies a row and decides where and how that row is stored. The first part of the primary key is the partition key, which chooses the node; any remaining parts are clustering columns, which order rows inside a partition.

Since there are no joins and efficient reads must name the partition key, you design each table around one specific query rather than around a normalized entity. The same data is often written into several tables, each shaped for a different read, and that duplication is expected rather than a smell.

---

## Detailed explanation with examples

### 1. Defining a table in CQL

- TODO: `CREATE TABLE`; columns and the `PRIMARY KEY` clause
- TODO: how CQL differs from SQL (no joins, no arbitrary WHERE)

### 2. CQL data types and collections

- TODO: scalar types; `list`, `set`, `map`
- TODO: `counter` columns and their constraints
- TODO: when collections are appropriate (small, bounded)

### 3. The primary key

- TODO: `PRIMARY KEY ((partition), clustering...)`
- TODO: partition key vs clustering columns
- TODO: uniqueness is per full primary key

### 4. Query-first table design

- TODO: start from the query, then design the table
- TODO: denormalize into one table per access pattern
- TODO: write to multiple tables (or use batches/MVs) to keep them in sync

### 5. Practical rule

```text
Design the primary key for a specific read, not for an entity.
Partition key chooses the node; clustering columns sort within it.
Expect to write the same data into several query tables.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: never rely on `ALLOW FILTERING`; model the query into the key
- TODO: keep collections small and bounded; avoid large maps/lists

### Operations and production

- TODO: validate primary keys against real query patterns before launch
- TODO: keep duplicated query tables consistent (logged batches, MVs, or app writes)

## References

- Official docs: https://cassandra.apache.org/doc/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [partition-and-clustering-keys.md](partition-and-clustering-keys.md)
