# ClickHouse — materialized views

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. An insert trigger, not a cache](#1-an-insert-trigger-not-a-cache)
  * [2. Aggregating rollups](#2-aggregating-rollups)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A ClickHouse materialized view is not a cached query result but an insert trigger: when rows arrive in a source table, the view's query runs on that batch and writes the result into a target table. Combined with an aggregating engine, this lets you maintain rollups — per-minute counts, running sums — incrementally as data lands, so dashboards read tiny pre-aggregated tables instead of scanning raw events.

Because the view only sees newly inserted rows, it computes on ingest rather than over history, which is what makes it cheap. Designing the right materialized views is how you keep analytical queries fast as raw data grows.

---

## Detailed explanation with examples

### 1. An insert trigger, not a cache

- TODO: MV runs on inserted batches; writes to a target table
- TODO: only sees new rows (not historical backfill)

### 2. Aggregating rollups

- TODO: `AggregatingMergeTree` + `-State`/`-Merge` functions
- TODO: per-interval rollups for dashboards

### 3. Practical rule

```text
Use MVs to pre-aggregate on ingest; read small rollup tables for dashboards.
Remember MVs only process new inserts — backfill separately.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: design rollup MVs for known dashboard queries

### Operations and production

- TODO: plan backfill for historical data; monitor MV target growth

## References

- Official docs: https://clickhouse.com/docs/en/sql-reference/statements/create/view/
- Overview: [fundamentals.md](fundamentals.md)
