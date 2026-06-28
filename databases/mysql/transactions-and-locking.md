# MySQL — transactions and locking

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Transactions under InnoDB](#1-transactions-under-innodb)
  * [2. Isolation levels](#2-isolation-levels)
  * [3. Row-level locking and deadlocks](#3-row-level-locking-and-deadlocks)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

InnoDB makes MySQL transactional, so statements can be grouped to commit or roll back together with full ACID guarantees. Its default isolation level is repeatable read, stricter than many other databases, and concurrency is managed with row-level locks rather than table locks.

Those locks can deadlock when transactions take them in different orders, so InnoDB detects deadlocks and rolls one transaction back. Keeping transactions short and accessing rows in a consistent order is how you avoid lock contention.

---

## Detailed explanation with examples

### 1. Transactions under InnoDB

- TODO: `START TRANSACTION`/`COMMIT`/`ROLLBACK`
- TODO: autocommit behavior

### 2. Isolation levels

- TODO: `REPEATABLE READ` (default), `READ COMMITTED`, others
- TODO: gap locks and phantom behavior

### 3. Row-level locking and deadlocks

- TODO: shared/exclusive row locks
- TODO: deadlock detection; `SHOW ENGINE INNODB STATUS`

### 4. Practical rule

```text
Keep transactions short; access rows in a consistent order to avoid deadlocks.
Choose READ COMMITTED if gap-lock contention hurts; expect deadlock retries.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: wrap multi-statement invariants in one transaction
- TODO: implement retry-on-deadlock in application code

### Operations and production

- TODO: monitor deadlocks and lock waits; tune isolation if needed
- TODO: avoid long-running transactions that block purge/undo

## References

- Official docs: https://dev.mysql.com/doc/
- Overview: [fundamentals.md](fundamentals.md)
