# SQLite — transactions and concurrency

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. ACID transactions](#1-acid-transactions)
  * [2. The single-writer model](#2-the-single-writer-model)
  * [3. WAL and busy timeout](#3-wal-and-busy-timeout)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

SQLite is fully ACID, wrapping changes in transactions that commit or roll back atomically against the database file. Its concurrency model is the main constraint: many connections can read at the same time, but only one can write, because a writer takes a lock on the database.

The write-ahead logging (WAL) journal mode relaxes this so readers and a writer can proceed concurrently, which is why WAL is the usual recommendation. When a writer cannot get the lock it gets `SQLITE_BUSY`, so setting a busy timeout is part of using it well.

---

## Detailed explanation with examples

### 1. ACID transactions

- TODO: `BEGIN`/`COMMIT`/`ROLLBACK`; atomic commit

### 2. The single-writer model

- TODO: many readers, one writer; database-level write lock

### 3. WAL and busy timeout

- TODO: `PRAGMA journal_mode = WAL`
- TODO: `busy_timeout` and handling `SQLITE_BUSY`

### 4. Practical rule

```text
Enable WAL for concurrent readers; set a busy_timeout for writers.
Do not expect high write concurrency from one file.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: batch writes inside a single transaction to reduce lock churn

### Operations and production

- TODO: set WAL + busy_timeout in connection setup; serialize writers in app design

## References

- Official docs: https://www.sqlite.org/lockingv3.html
- Overview: [fundamentals.md](fundamentals.md)
