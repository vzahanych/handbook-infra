# Elasticsearch — indices, shards, and segments

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Index, shard, segment](#1-index-shard-segment)
  * [2. Primaries and replicas](#2-primaries-and-replicas)
  * [3. Templates, aliases, data streams](#3-templates-aliases-data-streams)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

An Elasticsearch index is a collection of JSON documents, and physically it is split into shards that are distributed across the nodes of a cluster. Each shard is a self-contained Lucene index made up of immutable segments, and it comes in two roles: a primary shard that owns a slice of the data and replica shards that copy it for redundancy and read throughput.

Because a shard is the unit of distribution and Lucene segments are written once and merged in the background, the number and size of shards shapes both performance and resource use. For log and metrics data, index templates, aliases, and data streams manage the constant creation of new time-based indices.

---

## Detailed explanation with examples

### 1. Index, shard, segment

- TODO: index → shard → Lucene segment
- TODO: immutable segments; background merges

### 2. Primaries and replicas

- TODO: primary owns data; replicas copy it
- TODO: replicas serve reads and provide HA

### 3. Templates, aliases, data streams

- TODO: index templates; aliases for indirection
- TODO: data streams for time-series/logs

### 4. Practical rule

```text
Treat the shard as the unit of distribution; size it deliberately.
Use templates + aliases + data streams for rolling time-series indices.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: write through aliases; use data streams for append-only logs

### Operations and production

- TODO: avoid oversharding; monitor segment merges and shard counts

## References

- Official docs: https://www.elastic.co/guide/
- Overview: [fundamentals.md](fundamentals.md)
