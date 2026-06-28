# Elasticsearch — searching and aggregations

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

Queries are expressed in a JSON query DSL, and the central distinction is between the query context, which scores how well a document matches, and the filter context, which only asks yes or no and is cacheable and faster. A `bool` query composes clauses with must, should, and filter, letting you combine full-text relevance with exact constraints.

Relevance scoring uses the BM25 algorithm by default, ranking results by how well their terms match. Aggregations run alongside search to compute summaries — counts, averages, histograms, nested breakdowns — turning Elasticsearch into an analytics engine as well as a search one.

---

## Detailed explanation with examples

### 1. Query versus filter context

- TODO: scored queries vs cacheable filters
- TODO: `match` vs `term`

### 2. Bool queries and scoring

- TODO: `bool` with `must`/`should`/`filter`/`must_not`
- TODO: BM25 relevance

### 3. Aggregations

- TODO: metric and bucket aggregations; nesting

### 4. Practical rule

```text
Use filter context for exact constraints; query context only when you need scoring.
Run aggregations on keyword/numeric fields, not analyzed text.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer `filter` for exact matches; aggregate on `keyword`/numeric fields

### Operations and production

- TODO: watch expensive aggregations; cap result/aggregation sizes

## References

- Official docs: https://www.elastic.co/guide/
- Overview: [fundamentals.md](fundamentals.md)
