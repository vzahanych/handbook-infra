# TimescaleDB — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Still PostgreSQL](#1-still-postgresql)
  * [2. Hypertables and chunks](#2-hypertables-and-chunks)
  * [3. Indexes](#3-indexes)
  * [4. Continuous aggregates](#4-continuous-aggregates)
  * [5. Compression and retention](#5-compression-and-retention)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

TimescaleDB is a PostgreSQL extension for time-series data. It is still plain PostgreSQL — same SQL, types, indexes, and transactions — with one new idea: the hypertable, a table that is automatically split into time-based chunks behind the scenes. You query it like one big table and Timescale routes to the right chunks.

Splitting a hypertable into time-based chunks is what makes recent inserts and time-range queries fast, since the engine touches only the chunks a query spans and can compress or drop whole old chunks cheaply. None of this replaces PostgreSQL underneath, though: ordinary indexing, planning, and query rules still apply, and a chunk interval that is too large or too small undermines the very speedups chunking is meant to provide.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Still PostgreSQL

Why Timescale is an extension and everything Postgres still applies. See [still-postgresql.md](still-postgresql.md).

### 2. Hypertables and chunks

The hypertable abstraction, chunks, and chunk-interval sizing. See [hypertables-and-chunks.md](hypertables-and-chunks.md).

### 3. Indexes

Per-chunk indexes and time-series index patterns. See [indexes.md](indexes.md).

### 4. Continuous aggregates

Incrementally materialized rollups and refresh policies. See [continuous-aggregates.md](continuous-aggregates.md).

### 5. Compression and retention

Columnar chunk compression and chunk-dropping retention policies. See [compression-and-retention.md](compression-and-retention.md).

### 6. Practical rule

```text
It is Postgres — model and index normally, then add the time dimension.
Size chunks so recent data fits memory; compress and expire old chunks.
Pre-aggregate dashboards with continuous aggregates.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: make time the leading or secondary index column for range scans
- TODO: tune `chunk_time_interval` to your ingest and query window
- TODO: use continuous aggregates instead of repeated heavy `GROUP BY`

### Operations and production

- TODO: enable compression + retention policies for old chunks
- TODO: standard Postgres ops apply (vacuum, backups, replication)
- TODO: monitor chunk count, compression ratio, and bloat

## References

- Official docs: https://docs.tigerdata.com/
- Related: [postgresql/fundamentals.md](../postgresql/fundamentals.md)
