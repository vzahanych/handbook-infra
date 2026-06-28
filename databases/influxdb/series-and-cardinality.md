# InfluxDB — series and cardinality

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. What a series is](#1-what-a-series-is)
  * [2. The cardinality explosion](#2-the-cardinality-explosion)
  * [3. Keeping tags bounded](#3-keeping-tags-bounded)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A series in InfluxDB is the unique combination of a measurement and a particular set of tag values, and the total number of series — the cardinality — is the single biggest driver of an instance's memory use and performance. Because every distinct tag-value combination creates a new series, putting a high-variety value such as a user id, request id, or timestamp into a tag causes a cardinality explosion that can bring the database to its knees.

The discipline is to keep tag values bounded and low-cardinality, and to push anything unbounded into fields instead. Watching series cardinality is to InfluxDB what watching partition size is to Cassandra.

---

## Detailed explanation with examples

### 1. What a series is

- TODO: measurement + unique tag-set = one series

### 2. The cardinality explosion

- TODO: high-variety tags → millions of series → OOM

### 3. Keeping tags bounded

- TODO: ids/timestamps belong in fields, not tags

### 4. Practical rule

```text
Keep tag-set cardinality bounded; never tag by id/request/timestamp.
Monitor total series count.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: bound tag cardinality by design; review new tags for variety

### Operations and production

- TODO: monitor series cardinality and memory; alert before limits

## References

- Official docs: https://docs.influxdata.com/
- Overview: [fundamentals.md](fundamentals.md)
