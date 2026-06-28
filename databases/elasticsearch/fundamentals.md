# Elasticsearch — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Indices shards and segments](#1-indices-shards-and-segments)
  * [2. Documents and mappings](#2-documents-and-mappings)
  * [3. The inverted index](#3-the-inverted-index)
  * [4. Searching and aggregations](#4-searching-and-aggregations)
  * [5. Sharding and scaling](#5-sharding-and-scaling)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Elasticsearch is a distributed search and analytics engine. It stores JSON documents in an index, and each index is split into shards that are spread and replicated across nodes. Search is fast because every text field is broken into terms and stored in an inverted index that maps each term back to the documents that contain it.

The mapping is what makes or breaks an index: it decides how each field is typed and analyzed, and that in turn fixes what you can search, sort, and aggregate later. Most of a mapping cannot be changed once the index holds data, so these choices are effectively permanent. The one that trips people up most is `text` versus `keyword` — `text` is analyzed into terms for full-text search, while `keyword` is stored whole for exact filters, sorting, and aggregations — and a field often needs both.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Indices shards and segments

Index → shard → Lucene segment, primaries/replicas, templates and data streams. See [indices-shards-and-segments.md](indices-shards-and-segments.md).

### 2. Documents and mappings

Documents, mappings, dynamic vs explicit, and `text` vs `keyword`. See [documents-and-mappings.md](documents-and-mappings.md).

### 3. The inverted index

Terms-to-documents, analysis/analyzers, and doc values. See [the-inverted-index.md](the-inverted-index.md).

### 4. Searching and aggregations

Query vs filter context, `bool` queries, BM25, and aggregations. See [searching-and-aggregations.md](searching-and-aggregations.md).

### 5. Sharding and scaling

Shard sizing, replicas, and ILM for time-series. See [sharding-and-scaling.md](sharding-and-scaling.md).

### 6. Practical rule

```text
Define the mapping before you index at scale.
Use text for full-text, keyword for filters/aggregations/sorting.
Size shards (tens of GB each); use ILM for rolling time-series indices.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer explicit mappings; disable dynamic mapping where risky
- TODO: pick `text` vs `keyword` per use; use `filter` context for exact matches
- TODO: avoid over-nesting; model for the queries you run

### Operations and production

- TODO: keep shards reasonably sized; avoid shard explosion
- TODO: use ILM + data streams + aliases for logs/metrics
- TODO: monitor heap, JVM GC, cluster health (green/yellow/red), hot threads

## References

- Official docs: https://www.elastic.co/guide/
- Related: [opensearch/fundamentals.md](../opensearch/fundamentals.md)
