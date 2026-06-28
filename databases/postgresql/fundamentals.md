# PostgreSQL — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Cluster database and schema](#1-cluster-database-and-schema)
  * [2. Tables and data types](#2-tables-and-data-types)
  * [3. Keys and relationships](#3-keys-and-relationships)
  * [4. Indexes](#4-indexes)
  * [5. Transactions and MVCC](#5-transactions-and-mvcc)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

PostgreSQL is a relational database. It stores data in tables, tables live in schemas, and schemas live inside a named database. One running server can hold many databases, but a single connection talks to only one of them at a time.

A table defines the shape of your data through typed columns and constraints, while an index is a separate structure that only makes lookups faster without changing what the table means. That separation matters because every index you add also has to be maintained on each insert, update, and delete, so indexing every column quietly taxes your writes. Add indexes for the queries you actually run, and confirm they help rather than guessing.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Cluster database and schema

How a server holds databases, databases hold schemas, and `search_path` resolves names. See [cluster-database-and-schema.md](cluster-database-and-schema.md).

### 2. Tables and data types

Defining tables, PostgreSQL's rich type system, constraints, and partitioning. See [tables-and-data-types.md](tables-and-data-types.md).

### 3. Keys and relationships

Primary and unique keys, foreign keys and referential actions, surrogate vs natural keys. See [keys-and-relationships.md](keys-and-relationships.md).

### 4. Indexes

B-tree and the specialized index types, partial/expression/multicolumn indexes, and verifying usage. See [indexes.md](indexes.md).

### 5. Transactions and MVCC

ACID transactions, MVCC snapshots, isolation levels, and the dead-tuple/VACUUM cycle. See [transactions-and-mvcc.md](transactions-and-mvcc.md).

### 6. Practical rule

```text
Model the table for correctness first (types + constraints).
Add indexes for the queries you actually run.
Verify with EXPLAIN ANALYZE, not assumptions.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer correct types and constraints over application-side checks
- TODO: choose `timestamptz` over `timestamp`; `text` over `varchar(n)` unless bounded
- TODO: index foreign keys; use `EXPLAIN ANALYZE` before adding indexes

### Operations and production

- TODO: connection pooling (PgBouncer), tuning `shared_buffers`/`work_mem`
- TODO: autovacuum, backups (`pg_dump` vs PITR/WAL), replication
- TODO: monitor bloat, long transactions, and lock waits

## References

- Official docs: https://www.postgresql.org/docs/
- Related: [indexes.md](indexes.md), [transactions-and-mvcc.md](transactions-and-mvcc.md)
