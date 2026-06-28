# TimescaleDB — still PostgreSQL

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. An extension, not a fork](#1-an-extension-not-a-fork)
  * [2. What carries over](#2-what-carries-over)
  * [3. What the extension adds](#3-what-the-extension-adds)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

TimescaleDB is delivered as a PostgreSQL extension, not a separate database, so a Timescale instance is a Postgres instance with extra functions and table types loaded. Every Postgres feature still works — the same SQL, data types, indexes, joins, transactions, and tooling — which means your existing knowledge and drivers carry over directly.

What the extension adds is the hypertable and the time-series machinery built around it, layered on top of ordinary tables rather than replacing them. The first thing to internalize is therefore that nothing about Postgres goes away; Timescale only adds.

---

## Detailed explanation with examples

### 1. An extension, not a fork

- TODO: `CREATE EXTENSION timescaledb`
- TODO: same server, drivers, SQL

### 2. What carries over

- TODO: types, indexes, joins, transactions, backup/replication

### 3. What the extension adds

- TODO: hypertables, continuous aggregates, compression, retention

### 4. Practical rule

```text
Treat it as PostgreSQL first; add time-series features on top.
All Postgres skills and tools still apply.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: model and index like Postgres, then add the time dimension

### Operations and production

- TODO: standard Postgres ops (vacuum, backups, replication) still apply

## References

- Official docs: https://docs.tigerdata.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../postgresql/fundamentals.md](../postgresql/fundamentals.md)
