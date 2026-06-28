# SQLite — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. One file and no server](#1-one-file-and-no-server)
  * [2. Tables and type affinity](#2-tables-and-type-affinity)
  * [3. Keys and relationships](#3-keys-and-relationships)
  * [4. Indexes](#4-indexes)
  * [5. Transactions and concurrency](#5-transactions-and-concurrency)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

SQLite is a relational database that lives in a single file and runs inside your application with no separate server. You open the file, read and write with SQL, and close it. This makes it ideal for embedded use, local apps, and tests.

SQLite types data dynamically through type affinity, so a column declaration suggests a type rather than strictly enforcing it unless you opt into strict tables. Its other defining limit is concurrency: many connections can read at once, but only one can write at a time. That single-writer model is fine for embedded apps, local tools, and tests, and it is exactly why write-heavy multi-process workloads start hitting database locks.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. One file and no server

The in-process, single-file model, attached databases, and journal modes. See [one-file-and-no-server.md](one-file-and-no-server.md).

### 2. Tables and type affinity

Dynamic typing via affinity, rowid tables, and STRICT tables. See [tables-and-type-affinity.md](tables-and-type-affinity.md).

### 3. Keys and relationships

`INTEGER PRIMARY KEY` as the rowid alias and foreign keys (off by default). See [keys-and-relationships.md](keys-and-relationships.md).

### 4. Indexes

B-tree, partial, and expression indexes, and reading the query plan. See [indexes.md](indexes.md).

### 5. Transactions and concurrency

ACID transactions, the single-writer model, WAL, and busy timeout. See [transactions-and-concurrency.md](transactions-and-concurrency.md).

### 6. Practical rule

```text
Great for embedded, local, and test workloads — not for high write concurrency.
Enable WAL and foreign keys explicitly; consider STRICT tables for safety.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: turn on `PRAGMA foreign_keys = ON` per connection
- TODO: use `STRICT` tables when you want real type enforcement
- TODO: `INTEGER PRIMARY KEY` for the natural rowid alias

### Operations and production

- TODO: WAL mode + sensible `busy_timeout` for concurrent readers
- TODO: backup via `VACUUM INTO` or the online backup API
- TODO: keep the file on local disk (avoid network filesystems)

## References

- Official docs: https://www.sqlite.org/docs.html
- Related: [one-file-and-no-server.md](one-file-and-no-server.md)
