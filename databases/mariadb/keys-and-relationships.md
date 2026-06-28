# MariaDB — keys and relationships

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The clustered primary key](#1-the-clustered-primary-key)
  * [2. Foreign keys](#2-foreign-keys)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Keys behave as in MySQL: the InnoDB primary key is the clustered index, secondary indexes carry the primary key, and a small monotonic key keeps everything compact. Foreign keys under InnoDB enforce referential integrity with cascading actions.

The modeling rules are the same, so the main thing to track is which engine a table uses, since a non-InnoDB table may not support foreign keys at all.

---

## Detailed explanation with examples

### 1. The clustered primary key

- TODO: rows in PK order; secondary indexes carry the PK

### 2. Foreign keys

- TODO: `FOREIGN KEY` under InnoDB; referential actions
- TODO: engine support caveats

### 3. Practical rule

```text
Small monotonic primary key; foreign keys on InnoDB tables; index FK columns.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer ordered IDs over random UUIDv4 primary keys

### Operations and production

- TODO: confirm FK support matches the table's engine

## References

- Official docs: https://mariadb.com/kb/en/documentation/
- Overview: [fundamentals.md](fundamentals.md)
