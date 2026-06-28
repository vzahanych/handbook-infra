# MariaDB — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Structure and storage engines](#1-structure-and-storage-engines)
  * [2. Tables and data types](#2-tables-and-data-types)
  * [3. Keys and relationships](#3-keys-and-relationships)
  * [4. Indexes](#4-indexes)
  * [5. Transactions and concurrency](#5-transactions-and-concurrency)
  * [6. MySQL compatibility and differences](#6-mysql-compatibility-and-differences)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

MariaDB is a community fork of MySQL that keeps the same SQL and wire protocol. It has the same shape: a server holds databases, and databases hold tables, with behavior driven by the storage engine. Most MySQL knowledge transfers directly.

MariaDB defaults to InnoDB like MySQL, but it also ships engines and features MySQL does not have, such as Aria, ColumnStore, and system-versioned tables. Those additions are the reason to choose it, yet they also mean the two have drifted apart over time. Version numbering, JSON handling, and some built-in functions now behave differently, so verify anything non-trivial against your exact MariaDB version rather than assuming MySQL parity.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Structure and storage engines

Server/database/table layout and the extra engines (Aria, ColumnStore, Spider). See [structure-and-storage-engines.md](structure-and-storage-engines.md).

### 2. Tables and data types

Table definition, `utf8mb4`, and MariaDB extras like sequences and temporal tables. See [tables-and-data-types.md](tables-and-data-types.md).

### 3. Keys and relationships

The InnoDB clustered primary key and foreign keys. See [keys-and-relationships.md](keys-and-relationships.md).

### 4. Indexes

B-tree, composite, covering, and full-text/spatial indexes. See [indexes.md](indexes.md).

### 5. Transactions and concurrency

ACID under InnoDB, locking and deadlocks, and Galera cluster. See [transactions-and-concurrency.md](transactions-and-concurrency.md).

### 6. MySQL compatibility and differences

What stays compatible with MySQL and where the two diverge. See [mysql-compatibility-and-differences.md](mysql-compatibility-and-differences.md).

### 7. Practical rule

```text
Treat MariaDB as MySQL-compatible, but verify version-specific behavior.
Use InnoDB by default; reach for Aria/ColumnStore only for their niche.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: `utf8mb4`; surrogate PKs; leftmost-prefix indexes
- TODO: use MariaDB-only features (sequences, temporal tables) deliberately
- TODO: confirm JSON/function behavior matches the target version

### Operations and production

- TODO: tune InnoDB buffer pool; connection pooling
- TODO: backups (`mariabackup`), binlog, replication / Galera
- TODO: monitor slow queries, deadlocks, replication lag

## References

- Official docs: https://mariadb.com/kb/en/documentation/
- Related: [mysql/fundamentals.md](../mysql/fundamentals.md)
