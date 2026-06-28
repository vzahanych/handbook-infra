# OpenSearch — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Indices shards and segments](#1-indices-shards-and-segments)
  * [2. Documents and mappings](#2-documents-and-mappings)
  * [3. Searching and aggregations](#3-searching-and-aggregations)
  * [4. Sharding and scaling](#4-sharding-and-scaling)
  * [5. OpenSearch versus Elasticsearch](#5-opensearch-versus-elasticsearch)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

OpenSearch is the community fork of Elasticsearch 7.10. It keeps the same core data model: JSON documents in indices, split into shards, searched through an inverted index that is governed by mappings. Almost everything you know about Elasticsearch data modeling applies directly.

The differences from Elasticsearch are about licensing, bundled features, and some API naming rather than how data is stored or searched, so your indexing and query knowledge transfers intact. The catch is that OpenSearch has kept evolving since the 7.10 fork, so a specific Elasticsearch version's APIs, plugins, or settings may be renamed, missing, or behave differently here — lifecycle management is ISM rather than ILM, for one. Check the OpenSearch docs for anything version-specific instead of assuming the Elasticsearch shape.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Indices shards and segments

Index → shard → Lucene segment, primaries/replicas, templates and data streams. See [indices-shards-and-segments.md](indices-shards-and-segments.md).

### 2. Documents and mappings

Documents, mappings, dynamic vs explicit, and `text` vs `keyword`. See [documents-and-mappings.md](documents-and-mappings.md).

### 3. Searching and aggregations

Query vs filter context, `bool` queries, BM25, and aggregations. See [searching-and-aggregations.md](searching-and-aggregations.md).

### 4. Sharding and scaling

Shard sizing, replicas, and ISM lifecycle policies. See [sharding-and-scaling.md](sharding-and-scaling.md).

### 5. OpenSearch versus Elasticsearch

The fork, licensing, bundled plugins, and API/setting differences. See [opensearch-versus-elasticsearch.md](opensearch-versus-elasticsearch.md).

### 6. Practical rule

```text
Model exactly like Elasticsearch: explicit mappings, text vs keyword.
Use ISM (not ILM) for lifecycle; verify APIs against your OpenSearch version.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer explicit mappings; pick `text` vs `keyword` per use
- TODO: use `filter` context for exact matches and aggregations
- TODO: model around queries; avoid unnecessary nesting

### Operations and production

- TODO: size shards; use ISM + data streams + aliases for logs
- TODO: configure the bundled Security plugin (TLS, roles)
- TODO: monitor heap, GC, cluster health, hot threads

## References

- Official docs: https://opensearch.org/docs/
- Related: [elasticsearch/fundamentals.md](../elasticsearch/fundamentals.md)
