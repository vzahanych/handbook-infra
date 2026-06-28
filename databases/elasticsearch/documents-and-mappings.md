# Elasticsearch — documents and mappings

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

You index documents as JSON, each with an `_id` and its original body kept in `_source`, but how those documents become searchable is governed by the mapping. The mapping assigns a type and an analysis rule to every field, and it is largely fixed once an index holds data, so it is a decision you make carefully up front rather than change later.

Elasticsearch can infer a mapping dynamically from the first document it sees, but relying on that often produces the wrong types; explicit mappings are safer. The field choice that trips people up most is `text` versus `keyword` — `text` is analyzed into terms for full-text search, `keyword` is stored whole for exact filters, sorting, and aggregations — and a field frequently needs both.

---

## Detailed explanation with examples

### 1. Documents, _id, and _source

- TODO: indexing JSON; `_id`, `_source`

### 2. Dynamic versus explicit mapping

- TODO: dynamic inference pitfalls; explicit mappings
- TODO: types (`date`, numeric, `nested`, `geo_point`)

### 3. text versus keyword

- TODO: analyzed full-text vs exact keyword
- TODO: multi-fields (`text` + `keyword`)

### 4. Practical rule

```text
Define explicit mappings before indexing at scale.
text for full-text; keyword for filters/sort/aggregations; use both via multi-fields.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: disable risky dynamic mapping; choose `text`/`keyword` per field

### Operations and production

- TODO: changing mappings usually means reindexing — plan for it

## References

- Official docs: https://www.elastic.co/guide/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [the-inverted-index.md](the-inverted-index.md)
