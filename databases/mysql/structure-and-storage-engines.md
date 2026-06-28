# MySQL — structure and storage engines

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Server, database, table](#1-server-database-table)
  * [2. Storage engines](#2-storage-engines)
  * [3. Inspecting the server](#3-inspecting-the-server)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A MySQL server holds databases, each database holds tables, and in MySQL the words database and schema mean the same thing. What makes MySQL unusual is that a table's capabilities depend on its storage engine, the component that actually stores and indexes rows.

InnoDB is the modern default and the one to use: it provides transactions, foreign keys, and row-level locking. The older MyISAM engine lacks all three, so picking an engine is really picking a feature set.

---

## Detailed explanation with examples

### 1. Server, database, table

- TODO: server → database → table; database = schema
- TODO: `CREATE DATABASE`, `USE`

### 2. Storage engines

- TODO: InnoDB vs MyISAM feature comparison
- TODO: setting/checking `ENGINE=`

### 3. Inspecting the server

- TODO: `information_schema`, `performance_schema`
- TODO: `SHOW TABLE STATUS`

### 4. Practical rule

```text
Use InnoDB unless you have a proven, specific reason not to.
Treat database and schema as the same thing in MySQL.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: default every table to InnoDB
- TODO: avoid MyISAM for anything needing transactions/FKs

### Operations and production

- TODO: verify engine in migrations; watch for accidental MyISAM tables

## References

- Official docs: https://dev.mysql.com/doc/
- Overview: [fundamentals.md](fundamentals.md)
