# MariaDB — structure and storage engines

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Server, database, table](#1-server-database-table)
  * [2. The engine choices](#2-the-engine-choices)
  * [3. Picking an engine](#3-picking-an-engine)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

MariaDB has the same shape as MySQL — a server of databases, each a set of tables — and database and schema again mean the same thing. The storage engine still decides what a table can do, with InnoDB the default for transactional work.

MariaDB's distinguishing feature is the extra engines it ships: Aria as a crash-safe MyISAM successor, ColumnStore for analytics, and Spider for sharding across servers. You choose an engine per table to match the workload.

---

## Detailed explanation with examples

### 1. Server, database, table

- TODO: server → database → table; database = schema

### 2. The engine choices

- TODO: InnoDB (default), Aria, ColumnStore, Spider
- TODO: what each is for

### 3. Picking an engine

- TODO: transactional → InnoDB; analytics → ColumnStore
- TODO: setting/checking `ENGINE=`

### 4. Practical rule

```text
InnoDB by default; reach for Aria/ColumnStore/Spider only for their niche.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: default to InnoDB; use specialized engines deliberately

### Operations and production

- TODO: verify engine per table in migrations

## References

- Official docs: https://mariadb.com/kb/en/documentation/
- Overview: [fundamentals.md](fundamentals.md)
