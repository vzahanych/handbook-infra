# InfluxDB — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Buckets and measurements](#1-buckets-and-measurements)
  * [2. Tags and fields](#2-tags-and-fields)
  * [3. Series and cardinality](#3-series-and-cardinality)
  * [4. Line protocol and ingest](#4-line-protocol-and-ingest)
  * [5. Retention and downsampling](#5-retention-and-downsampling)
  * [6. Querying](#6-querying)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

InfluxDB is a database built for time-series data. Instead of tables and rows, it stores points, where each point has a measurement name, a set of tags, one or more fields, and a timestamp. Points live in a bucket that has a retention period, so old data expires on its own.

Everything turns on the split between tags and fields: tags are indexed and meant for filtering and grouping, while fields hold the measured values and are not indexed. That index is also the danger, because each unique combination of tag values is a separate series, so putting high-variety values like user IDs or request IDs into tags spawns millions of series and overwhelms the database. Keep tag values bounded and the rest follows. (Terminology and query language differ across 1.x, 2.x, and 3.x — note your version.)

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Buckets and measurements

Buckets, measurements, schema-on-write, and version terminology. See [buckets-and-measurements.md](buckets-and-measurements.md).

### 2. Tags and fields

The indexed-tags vs unindexed-fields split and timestamps. See [tags-and-fields.md](tags-and-fields.md).

### 3. Series and cardinality

What a series is and why cardinality is the key constraint. See [series-and-cardinality.md](series-and-cardinality.md).

### 4. Line protocol and ingest

The line protocol format, batching, and collection agents. See [line-protocol-and-ingest.md](line-protocol-and-ingest.md).

### 5. Retention and downsampling

Bucket retention and downsampling into longer-lived rollups. See [retention-and-downsampling.md](retention-and-downsampling.md).

### 6. Querying

InfluxQL/Flux/SQL by version and the range→filter→aggregate shape. See [querying.md](querying.md).

### 7. Practical rule

```text
Tags for what you filter/group by; fields for the measured values.
Keep tag cardinality bounded — never put IDs in tags.
Set retention and downsample old data to keep storage flat.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: decide tag vs field deliberately; bound tag cardinality
- TODO: batch writes; use consistent measurement/tag naming
- TODO: always query within a time `range` first

### Operations and production

- TODO: set bucket retention; downsample to rollup buckets
- TODO: monitor series cardinality and memory closely
- TODO: pick the version (1.x/2.x/3.x) deliberately; back up data

## References

- Official docs: https://docs.influxdata.com/
- Related: [timescaledb/fundamentals.md](../timescaledb/fundamentals.md)
