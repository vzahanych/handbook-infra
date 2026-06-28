# MySQL — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Structure and storage engines](#1-structure-and-storage-engines)
  * [2. Tables and data types](#2-tables-and-data-types)
  * [3. Keys and relationships](#3-keys-and-relationships)
  * [4. Indexes](#4-indexes)
  * [5. Transactions and locking](#5-transactions-and-locking)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

MySQL is a relational database where a server holds several databases, and each database holds tables. In MySQL the words database and schema mean the same thing. The behavior of a table — whether it supports transactions, foreign keys, and row locking — depends on its storage engine, and the modern default is InnoDB.

InnoDB stores each table as a clustered index ordered by its primary key, so the primary key you choose shapes how every row sits on disk and how every secondary index points back to it. A small, monotonic primary key keeps that layout compact, while a large or random one bloats every secondary index along with it. The engine choice matters just as much: only InnoDB gives you transactions and foreign keys, so reach for the older MyISAM engine only with a specific reason.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Structure and storage engines

How a server holds databases and tables, and how the storage engine decides a table's capabilities. See [structure-and-storage-engines.md](structure-and-storage-engines.md).

### 2. Tables and data types

Defining tables, the data types, and why `utf8mb4` and collation choices matter. See [tables-and-data-types.md](tables-and-data-types.md).

### 3. Keys and relationships

The InnoDB clustered primary key, unique keys, and foreign keys. See [keys-and-relationships.md](keys-and-relationships.md).

### 4. Indexes

B-tree indexes over the clustered key, leftmost-prefix composites, and covering indexes. See [indexes.md](indexes.md).

### 5. Transactions and locking

ACID under InnoDB, isolation levels, and row-level locking and deadlocks. See [transactions-and-locking.md](transactions-and-locking.md).

### 6. Practical rule

```text
Use InnoDB unless you have a proven reason not to.
Pick a small, monotonic primary key (secondary indexes carry it).
Design composite indexes left to right for your WHERE clauses.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: always `utf8mb4`; avoid `utf8` (3-byte) legacy charset
- TODO: prefer `INT`/`BIGINT` surrogate PKs; respect leftmost-prefix in indexes
- TODO: verify plans with `EXPLAIN`; avoid functions on indexed columns in WHERE

### Operations and production

- TODO: tune `innodb_buffer_pool_size`; connection pooling
- TODO: backups (`mysqldump`, `xtrabackup`), binlog, replication
- TODO: monitor slow query log, deadlocks, replication lag

## References

- Official docs: https://dev.mysql.com/doc/
- Related: [mariadb/fundamentals.md](../mariadb/fundamentals.md)
