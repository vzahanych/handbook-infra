# InfluxDB — querying

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The query languages by version](#1-the-query-languages-by-version)
  * [2. Range, filter, aggregate](#2-range-filter-aggregate)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

How you query InfluxDB depends heavily on the version, which is the main thing to know going in. The 1.x line uses InfluxQL, a SQL-like language; 2.x introduced Flux, a functional pipeline language built around composing operations; and 3.x adds native SQL.

Whatever the dialect, an efficient query starts by narrowing to a time range, then filters by tags, then aggregates over time windows, because the time range and tag index are what make the scan cheap. Always bounding the query in time is the habit that keeps it fast.

---

## Detailed explanation with examples

### 1. The query languages by version

- TODO: InfluxQL (1.x), Flux (2.x), SQL (3.x)

### 2. Range, filter, aggregate

- TODO: `range` → `filter` → `aggregateWindow` (Flux)
- TODO: equivalent shapes in InfluxQL/SQL

### 3. Practical rule

```text
Always bound queries by time first, then filter by tags.
Aggregate over windows rather than scanning raw points.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: filter on tags (indexed), not fields; window aggregations

### Operations and production

- TODO: cap unbounded queries; watch slow/expensive queries

## References

- Official docs: https://docs.influxdata.com/
- Overview: [fundamentals.md](fundamentals.md)
