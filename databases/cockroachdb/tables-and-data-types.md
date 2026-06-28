# CockroachDB — tables and data types

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. PostgreSQL-compatible SQL](#1-postgresql-compatible-sql)
  * [2. Data types](#2-data-types)
  * [3. Compatibility gaps](#3-compatibility-gaps)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

CockroachDB tables are written with PostgreSQL-compatible SQL and types, so `CREATE TABLE`, common column types, and constraints look familiar. The compatibility is deep but not total: some PostgreSQL features are missing or behave differently, so you check the docs rather than assume parity.

Because every table is ultimately key-value ranges, the choices you make in a table definition — especially the primary key — have distribution consequences that pure Postgres does not. Treat the SQL as familiar but the storage as distributed.

---

## Detailed explanation with examples

### 1. PostgreSQL-compatible SQL

- TODO: `CREATE TABLE`, constraints, the pgwire protocol

### 2. Data types

- TODO: common Postgres-compatible types; `UUID`, `JSONB`

### 3. Compatibility gaps

- TODO: unsupported/divergent Postgres features
- TODO: checking the compatibility docs

### 4. Practical rule

```text
Write Postgres-style SQL, but verify feature support and mind key distribution.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: don't assume every Postgres extension/feature exists

### Operations and production

- TODO: test schema migrations against the target CockroachDB version

## References

- Official docs: https://www.cockroachlabs.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [keys-and-avoiding-hotspots.md](keys-and-avoiding-hotspots.md)
