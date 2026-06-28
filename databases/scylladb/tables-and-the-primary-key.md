# ScyllaDB — tables and the primary key

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Defining a table in CQL](#1-defining-a-table-in-cql)
  * [2. The primary key](#2-the-primary-key)
  * [3. Query-first design](#3-query-first-design)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A ScyllaDB table is defined in CQL exactly as in Cassandra, with typed columns and a primary key that both identifies a row and decides its placement. The first component is the partition key, which selects the node and now also the core; any remaining components are clustering columns that order rows within the partition.

As in Cassandra, there are no joins and efficient reads must supply the partition key, so you design one table per query and accept denormalization. Everything you know about Cassandra table design applies directly.

---

## Detailed explanation with examples

### 1. Defining a table in CQL

- TODO: `CREATE TABLE`; CQL types and collections

### 2. The primary key

- TODO: partition key + clustering columns
- TODO: placement to node and shard

### 3. Query-first design

- TODO: one table per query; denormalization

### 4. Practical rule

```text
Design the primary key for a specific read; partition key first.
Expect to maintain several query tables.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: avoid `ALLOW FILTERING`; model queries into the key

### Operations and production

- TODO: validate keys against real query patterns

## References

- Official docs: https://docs.scylladb.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [partition-and-clustering-keys.md](partition-and-clustering-keys.md)
