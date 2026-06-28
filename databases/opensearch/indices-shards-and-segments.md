# OpenSearch — indices, shards, and segments

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

OpenSearch inherits the Elasticsearch storage model wholesale: an index is a set of JSON documents split into shards spread across the cluster, where each shard is a Lucene index of immutable segments, in primary and replica roles. A primary shard owns a portion of the data and replicas copy it for redundancy and read scaling, exactly as in Elasticsearch.

Segment immutability and background merges mean shard count and size drive performance and resource use the same way. For logs and metrics, index templates, aliases, and data streams handle the rolling creation of time-based indices.

---

## Detailed explanation with examples

### 1. Index, shard, segment

- TODO: index → shard → Lucene segment; immutable segments

### 2. Primaries and replicas

- TODO: primary owns data; replicas copy for HA + reads

### 3. Templates, aliases, data streams

- TODO: templates, aliases, data streams for time-series

### 4. Practical rule

```text
Same model as Elasticsearch: shard is the unit of distribution, size it deliberately.
Use templates + aliases + data streams for rolling indices.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: write through aliases; data streams for append-only logs

### Operations and production

- TODO: avoid oversharding; monitor merges and shard counts

## References

- Official docs: https://opensearch.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
