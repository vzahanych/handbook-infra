# MariaDB — tables and data types

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Defining a table](#1-defining-a-table)
  * [2. Sequences](#2-sequences)
  * [3. System-versioned tables](#3-system-versioned-tables)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A MariaDB table is defined like a MySQL one, with typed columns, `AUTO_INCREMENT`, and `utf8mb4` as the character set to use. Where it goes further is in features MySQL lacks: real `SEQUENCE` objects for generating numbers, and system-versioned (temporal) tables that keep history automatically so you can query a row as it was at any past time.

These extras are reasons to choose MariaDB, but they also make schemas less portable back to MySQL.

---

## Detailed explanation with examples

### 1. Defining a table

- TODO: `CREATE TABLE`, types, `utf8mb4`, `AUTO_INCREMENT`

### 2. Sequences

- TODO: `CREATE SEQUENCE`; vs `AUTO_INCREMENT`

### 3. System-versioned tables

- TODO: `WITH SYSTEM VERSIONING`
- TODO: `FOR SYSTEM_TIME AS OF` queries

### 4. Practical rule

```text
Use utf8mb4 and precise types; adopt sequences/temporal tables when they earn it.
Remember these features reduce MySQL portability.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: use temporal tables for audit/history instead of hand-rolled history tables

### Operations and production

- TODO: account for history growth on system-versioned tables

## References

- Official docs: https://mariadb.com/kb/en/documentation/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [indexes.md](indexes.md)
