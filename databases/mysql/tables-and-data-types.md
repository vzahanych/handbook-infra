# MySQL — tables and data types

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Defining a table](#1-defining-a-table)
  * [2. Data types](#2-data-types)
  * [3. Character sets and collations](#3-character-sets-and-collations)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A MySQL table is a list of typed columns, and the type and character-set choices have real consequences. Use `INT`/`BIGINT` for surrogate keys, `DECIMAL` for money, and `DATETIME` or `TIMESTAMP` for time, and always choose the `utf8mb4` character set so four-byte characters like emoji store correctly — the legacy `utf8` is only three bytes.

`AUTO_INCREMENT` gives you generated primary keys, and `JSON` and `ENUM` cover semi-structured and constrained values. Getting types and collation right at table creation avoids painful migrations later.

---

## Detailed explanation with examples

### 1. Defining a table

- TODO: `CREATE TABLE`, `NOT NULL`, `DEFAULT`, `AUTO_INCREMENT`

### 2. Data types

- TODO: `INT`/`BIGINT`, `DECIMAL`, `VARCHAR`, `DATETIME` vs `TIMESTAMP`
- TODO: `JSON`, `ENUM` and their trade-offs

### 3. Character sets and collations

- TODO: always `utf8mb4`; avoid 3-byte `utf8`
- TODO: collation and comparison/sort behavior

### 4. Practical rule

```text
Use utf8mb4 everywhere; DECIMAL for money; the smallest correct integer type.
Set types and collation at creation — migrations on big tables are costly.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer `utf8mb4`; avoid storing money as float
- TODO: use `ENUM`/`JSON` deliberately, not as a default

### Operations and production

- TODO: plan online schema changes (gh-ost/pt-osc) for large tables

## References

- Official docs: https://dev.mysql.com/doc/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [indexes.md](indexes.md)
