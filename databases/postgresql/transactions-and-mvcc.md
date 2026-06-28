# PostgreSQL — transactions and MVCC

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Transactions and ACID](#1-transactions-and-acid)
  * [2. MVCC snapshots](#2-mvcc-snapshots)
  * [3. Isolation levels](#3-isolation-levels)
  * [4. Dead tuples and VACUUM](#4-dead-tuples-and-vacuum)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A transaction groups statements so they either all commit or all roll back, giving PostgreSQL its ACID guarantees. Concurrency is handled by MVCC, multiversion concurrency control, where each transaction sees a consistent snapshot and writers do not block readers because updates create new row versions instead of overwriting old ones.

Those old versions, called dead tuples, accumulate until `VACUUM` reclaims them, so understanding vacuum and bloat is part of running PostgreSQL well. Isolation levels let you choose how strict that snapshot is, from read committed up to serializable.

---

## Detailed explanation with examples

### 1. Transactions and ACID

- TODO: `BEGIN`/`COMMIT`/`ROLLBACK`; savepoints
- TODO: atomicity and durability guarantees

### 2. MVCC snapshots

- TODO: row versions; readers don't block writers
- TODO: visibility and snapshot timing

### 3. Isolation levels

- TODO: read committed (default), repeatable read, serializable
- TODO: anomalies each level prevents

### 4. Dead tuples and VACUUM

- TODO: how updates/deletes create dead tuples
- TODO: autovacuum, `VACUUM`, bloat, `VACUUM FULL`

### 5. Practical rule

```text
Keep transactions short; long ones hold snapshots and block vacuum.
Pick the lowest isolation level that prevents the anomalies you care about.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: wrap multi-statement invariants in a transaction
- TODO: use serializable + retry for strict correctness paths

### Operations and production

- TODO: tune autovacuum for high-churn tables; monitor bloat
- TODO: alert on long-running transactions and lock waits

## References

- Official docs: https://www.postgresql.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
