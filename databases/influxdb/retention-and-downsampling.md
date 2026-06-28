# InfluxDB — retention and downsampling

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Retention periods](#1-retention-periods)
  * [2. Downsampling tasks](#2-downsampling-tasks)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Time-series data loses value as it ages, and InfluxDB handles this with retention and downsampling working together. Each bucket has a retention period after which old data is automatically expired, so raw high-resolution points do not accumulate forever.

Before they expire, a task — a continuous query in 1.x or a scheduled task in 2.x — can downsample them into coarser rollups, for example turning per-second readings into per-hour averages stored in a longer-lived bucket. The combination keeps storage flat while preserving the long-term trends you actually care about.

---

## Detailed explanation with examples

### 1. Retention periods

- TODO: per-bucket retention; automatic expiry

### 2. Downsampling tasks

- TODO: continuous queries (1.x) / tasks (2.x)
- TODO: raw bucket → rollup bucket with longer retention

### 3. Practical rule

```text
Set short retention on raw data; downsample to longer-lived rollups.
This keeps storage flat while preserving trends.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: separate raw vs rollup buckets with different retention

### Operations and production

- TODO: schedule downsampling tasks; verify they keep up with ingest

## References

- Official docs: https://docs.influxdata.com/
- Overview: [fundamentals.md](fundamentals.md)
