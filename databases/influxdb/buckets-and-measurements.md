# InfluxDB — buckets and measurements

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Buckets](#1-buckets)
  * [2. Measurements and schema-on-write](#2-measurements-and-schema-on-write)
  * [3. Version terminology](#3-version-terminology)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

InfluxDB groups data into buckets, each a named store with its own retention period, and within a bucket you write to measurements, which play the role of a table name. There is no schema to define up front: measurements, tags, and fields come into existence the first time you write a point that uses them, a model called schema-on-write.

The exact terminology shifts across versions — 1.x speaks of databases and retention policies, 2.x of organizations and buckets, 3.x reintroduces SQL — so the first thing to pin down is which version you are on. The shared idea across all of them is a time-stamped point living in a named measurement inside a retention-bounded container.

---

## Detailed explanation with examples

### 1. Buckets

- TODO: bucket = store + retention period
- TODO: org → bucket (2.x); database → RP (1.x)

### 2. Measurements and schema-on-write

- TODO: measurement ≈ table; created on first write

### 3. Version terminology

- TODO: 1.x vs 2.x vs 3.x naming and query language

### 4. Practical rule

```text
Pin your version first — terminology and query language differ.
One point = measurement + tags + fields + timestamp in a retention-bounded bucket.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: name measurements consistently; group by bucket + retention need

### Operations and production

- TODO: choose the version deliberately; set bucket retention up front

## References

- Official docs: https://docs.influxdata.com/
- Overview: [fundamentals.md](fundamentals.md)
