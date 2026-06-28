# PostgreSQL — tables and data types

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Defining a table](#1-defining-a-table)
  * [2. The type system](#2-the-type-system)
  * [3. Constraints](#3-constraints)
  * [4. Partitioning](#4-partitioning)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A table is a set of rows with a fixed list of typed columns, and PostgreSQL's strong, rich type system is one of its main strengths. Beyond the usual integers, text, and timestamps it offers `numeric` for exact decimals, `jsonb` for semi-structured data, arrays, and ranges, so the right type often removes the need for application-side parsing.

Columns carry constraints — `NOT NULL`, `DEFAULT`, `CHECK`, `UNIQUE` — that let the database enforce rules no application bug can bypass. Choosing precise types and constraints up front is what keeps the data trustworthy as it grows.

---

## Detailed explanation with examples

### 1. Defining a table

- TODO: `CREATE TABLE`, columns, `NOT NULL`, `DEFAULT`
- TODO: generated/identity columns

### 2. The type system

- TODO: `int`/`bigint`, `text`, `numeric`, `timestamptz`
- TODO: `jsonb`, arrays, ranges, enums
- TODO: prefer `timestamptz` over `timestamp`

### 3. Constraints

- TODO: `CHECK`, `UNIQUE`, `NOT NULL`
- TODO: enforcing invariants in the schema

### 4. Partitioning

- TODO: declarative range/list/hash partitioning
- TODO: when partitioning helps

### 5. Practical rule

```text
Pick the most precise type; let constraints enforce invariants.
Default to timestamptz and text; reach for jsonb only for truly dynamic data.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: model with strict types + constraints over app-side checks
- TODO: use `jsonb` deliberately, not as a schema escape hatch

### Operations and production

- TODO: plan partitioning for very large/time-series tables
- TODO: watch for table bloat on heavy-update tables

## References

- Official docs: https://www.postgresql.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [indexes.md](indexes.md)
