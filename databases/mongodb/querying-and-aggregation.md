# MongoDB — querying and aggregation

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Filters and projection](#1-filters-and-projection)
  * [2. The aggregation pipeline](#2-the-aggregation-pipeline)
  * [3. Update operators](#3-update-operators)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

MongoDB queries are documents themselves: you pass a filter describing the fields to match and a projection choosing which fields to return. For anything beyond simple lookups, the aggregation pipeline transforms data through ordered stages such as `$match` to filter, `$group` to summarize, and `$lookup` to join across collections.

Updates use operators like `$set`, `$inc`, and `$push` to change parts of a document in place rather than rewriting it. Learning the pipeline is what unlocks reporting and analytics without exporting data elsewhere.

---

## Detailed explanation with examples

### 1. Filters and projection

- TODO: query filter documents; operators (`$gt`, `$in`)
- TODO: projection to limit returned fields

### 2. The aggregation pipeline

- TODO: `$match`, `$group`, `$sort`, `$project`, `$lookup`
- TODO: `$match` early to use indexes

### 3. Update operators

- TODO: `$set`, `$inc`, `$push`, `$pull`
- TODO: upserts

### 4. Practical rule

```text
Put `$match` first so the pipeline can use indexes.
Update in place with operators; don't read-modify-write whole documents.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: filter early; project only needed fields; index pipeline `$match`/`$sort`

### Operations and production

- TODO: watch for unindexed `$lookup`/`$sort`; cap pipeline memory

## References

- Official docs: https://www.mongodb.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
