# OpenSearch — searching and aggregations

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Query versus filter context](#1-query-versus-filter-context)
  * [2. Bool queries and scoring](#2-bool-queries-and-scoring)
  * [3. Aggregations](#3-aggregations)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

OpenSearch uses the same JSON query DSL as Elasticsearch, with the same split between scored query context and cacheable filter context, and the same `bool` query for combining clauses. Relevance scoring is BM25 by default, and aggregations provide the metric and bucket summaries that make it an analytics engine.

Because the fork predates recent Elasticsearch changes, very new query features may differ or be absent, so check the OpenSearch reference. For the common cases, queries written for one work on the other.

---

## Detailed explanation with examples

### 1. Query versus filter context

- TODO: scored queries vs cacheable filters; `match` vs `term`

### 2. Bool queries and scoring

- TODO: `bool` clauses; BM25 relevance

### 3. Aggregations

- TODO: metric and bucket aggregations; nesting

### 4. Practical rule

```text
Use filter context for exact constraints; aggregate on keyword/numeric fields.
Verify newer query features against the OpenSearch reference.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer `filter` for exact matches; aggregate on `keyword`/numeric

### Operations and production

- TODO: watch expensive aggregations; cap result/aggregation sizes

## References

- Official docs: https://opensearch.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
