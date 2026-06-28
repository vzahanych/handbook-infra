# TimescaleDB — continuous aggregates

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Incrementally materialized rollups](#1-incrementally-materialized-rollups)
  * [2. Refresh policies](#2-refresh-policies)
  * [3. Real-time aggregation](#3-real-time-aggregation)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A continuous aggregate is TimescaleDB's answer to repeatedly running the same heavy `GROUP BY` over a time range: it is a materialized rollup that refreshes incrementally as new data arrives, rather than recomputing from scratch. You define it once with a `time_bucket` aggregation, and a refresh policy keeps it up to date by processing only the recent buckets that changed.

Dashboards then read the small aggregate instead of scanning millions of raw rows, and real-time mode can blend the materialized result with the newest unmaterialized data. This is the feature that keeps time-series dashboards fast as the underlying table grows.

---

## Detailed explanation with examples

### 1. Incrementally materialized rollups

- TODO: `CREATE MATERIALIZED VIEW ... WITH (timescaledb.continuous)`
- TODO: `time_bucket` aggregation

### 2. Refresh policies

- TODO: `add_continuous_aggregate_policy`; refreshing recent buckets

### 3. Real-time aggregation

- TODO: blending materialized + latest raw data

### 4. Practical rule

```text
Replace repeated heavy GROUP BY with a continuous aggregate.
Add a refresh policy; read the rollup in dashboards.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: build continuous aggregates for known dashboard queries

### Operations and production

- TODO: tune refresh policy window/lag; monitor refresh duration

## References

- Official docs: https://docs.tigerdata.com/
- Overview: [fundamentals.md](fundamentals.md)
