# OpenSearch — documents and mappings

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Documents, _id, and _source](#1-documents-_id-and-_source)
  * [2. Dynamic versus explicit mapping](#2-dynamic-versus-explicit-mapping)
  * [3. text versus keyword](#3-text-versus-keyword)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

As in Elasticsearch, you index JSON documents with an `_id` and a stored `_source`, and the mapping decides each field's type and analysis. Mappings are largely immutable once data exists, so explicit mappings beat relying on dynamic inference, and the `text` versus `keyword` decision is the same critical one — analyzed full-text versus exact value for filters and aggregations.

The behavior carries over directly from Elasticsearch, so existing mapping knowledge applies. Differences from Elasticsearch are mostly in tooling and naming, not in how mappings work.

---

## Detailed explanation with examples

### 1. Documents, _id, and _source

- TODO: indexing JSON; `_id`, `_source`

### 2. Dynamic versus explicit mapping

- TODO: dynamic pitfalls; explicit mappings; field types

### 3. text versus keyword

- TODO: analyzed vs exact; multi-fields

### 4. Practical rule

```text
Define explicit mappings; text for full-text, keyword for filters/sort/aggregations.
Mapping behavior matches Elasticsearch.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: disable risky dynamic mapping; choose `text`/`keyword` per field

### Operations and production

- TODO: mapping changes usually mean reindexing — plan for it

## References

- Official docs: https://opensearch.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [opensearch-versus-elasticsearch.md](opensearch-versus-elasticsearch.md)
