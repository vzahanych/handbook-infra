# MongoDB — indexes

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Single-field and compound indexes](#1-single-field-and-compound-indexes)
  * [2. Multikey indexes](#2-multikey-indexes)
  * [3. Specialized indexes](#3-specialized-indexes)
  * [4. Confirming usage with explain](#4-confirming-usage-with-explain)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Indexes in MongoDB serve the same purpose as elsewhere — finding documents without scanning the whole collection — and the `_id` field is indexed automatically. You can build single-field indexes, compound indexes that follow a leftmost-prefix rule like relational composites, and multikey indexes that transparently index each element of an array field.

Specialized types cover text search, geospatial queries, hashed sharding keys, wildcard fields, and TTL indexes that expire documents after a set time. The `explain()` method confirms whether a query uses an index or falls back to a collection scan.

---

## Detailed explanation with examples

### 1. Single-field and compound indexes

- TODO: leftmost-prefix rule; matching query + sort

### 2. Multikey indexes

- TODO: indexing array elements; caveats

### 3. Specialized indexes

- TODO: text, geospatial, hashed, wildcard
- TODO: TTL indexes for expiry; unique/partial indexes

### 4. Confirming usage with explain

- TODO: `explain()`; spotting `COLLSCAN`

### 5. Practical rule

```text
Build compound indexes that match filter + sort; verify with explain().
Use TTL indexes for expiring data; partial indexes to shrink index size.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: index for actual queries; respect leftmost-prefix; avoid over-indexing

### Operations and production

- TODO: build indexes in the background/rolling; watch index size vs RAM

## References

- Official docs: https://www.mongodb.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
