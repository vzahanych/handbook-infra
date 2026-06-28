# CockroachDB — multi-region tables

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Table localities](#1-table-localities)
  * [2. Survival goals](#2-survival-goals)
  * [3. Data residency](#3-data-residency)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

For clusters spread across regions, CockroachDB lets you control where data lives and how it survives failure through table localities. A regional table is pinned to one region for low local latency, a global table is optimized for fast reads everywhere at the cost of slower writes, and a regional-by-row table places each row in a region chosen by a column, which suits per-user data residency.

Alongside locality you set a survival goal: tolerate a zone failure, or the harder target of surviving a whole region going down. These settings turn geography into a schema decision rather than an operational afterthought.

---

## Detailed explanation with examples

### 1. Table localities

- TODO: regional, global, regional-by-row
- TODO: latency trade-offs of each

### 2. Survival goals

- TODO: zone survival vs region survival
- TODO: replica placement implications

### 3. Data residency

- TODO: regional-by-row for per-user/per-tenant residency

### 4. Practical rule

```text
Pick locality per table by read/write latency needs.
Choose the survival goal your SLA requires; it costs replicas.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: use regional-by-row for residency; global tables for read-mostly reference data

### Operations and production

- TODO: define regions explicitly; verify survival goals match failure tolerance

## References

- Official docs: https://www.cockroachlabs.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
