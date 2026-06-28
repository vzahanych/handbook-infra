# MariaDB — transactions and concurrency

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Transactions under InnoDB](#1-transactions-under-innodb)
  * [2. Row-level locking and deadlocks](#2-row-level-locking-and-deadlocks)
  * [3. Galera cluster](#3-galera-cluster)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

InnoDB gives MariaDB ACID transactions, isolation levels, and row-level locking just as in MySQL, so the day-to-day concurrency model is the same: keep transactions short and take locks in a consistent order to avoid deadlocks.

Where MariaDB differs is in clustering: its high-availability story centers on Galera Cluster, a synchronous multi-master replication layer, which changes how writes commit across nodes. Knowing whether you run plain replication or Galera matters for how transactions behave under failure.

---

## Detailed explanation with examples

### 1. Transactions under InnoDB

- TODO: `START TRANSACTION`/`COMMIT`/`ROLLBACK`; isolation levels

### 2. Row-level locking and deadlocks

- TODO: lock types; deadlock detection and retries

### 3. Galera cluster

- TODO: synchronous multi-master; certification-based replication
- TODO: write conflicts and `wsrep` behavior

### 4. Practical rule

```text
Keep transactions short; retry on deadlock.
On Galera, expect write certification conflicts and design for them.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: wrap invariants in transactions; implement deadlock retries

### Operations and production

- TODO: choose plain replication vs Galera deliberately; monitor `wsrep` state
- TODO: avoid long transactions that stall the cluster

## References

- Official docs: https://mariadb.com/kb/en/documentation/
- Overview: [fundamentals.md](fundamentals.md)
