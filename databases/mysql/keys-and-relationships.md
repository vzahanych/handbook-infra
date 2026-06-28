# MySQL — keys and relationships

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The clustered primary key](#1-the-clustered-primary-key)
  * [2. Unique keys](#2-unique-keys)
  * [3. Foreign keys](#3-foreign-keys)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Keys in MySQL identify rows and connect tables, but under InnoDB they also shape physical storage. The primary key is the clustered index, meaning rows are physically stored in primary-key order, and every secondary index stores the primary key as its pointer back to the row.

Because of that, a small monotonic primary key keeps both the table and its secondary indexes compact, while a large or random one inflates all of them. Foreign keys, available only under InnoDB, enforce referential integrity with cascading actions.

---

## Detailed explanation with examples

### 1. The clustered primary key

- TODO: rows stored in PK order; secondary indexes carry the PK
- TODO: small monotonic PK vs random/large PK

### 2. Unique keys

- TODO: `UNIQUE` constraints and multi-column uniqueness
- TODO: NULL handling in unique indexes

### 3. Foreign keys

- TODO: `FOREIGN KEY` (InnoDB only), referential actions
- TODO: index the referencing column

### 4. Practical rule

```text
Pick a small, monotonic primary key — every secondary index carries it.
Use foreign keys under InnoDB; index the referencing columns.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer `BIGINT AUTO_INCREMENT` or ordered IDs over random UUIDv4 PKs
- TODO: add unique constraints for natural identifiers

### Operations and production

- TODO: foreign key checks add write cost; validate large FK additions

## References

- Official docs: https://dev.mysql.com/doc/
- Overview: [fundamentals.md](fundamentals.md)
