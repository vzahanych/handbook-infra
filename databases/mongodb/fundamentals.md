# MongoDB — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Databases collections and documents](#1-databases-collections-and-documents)
  * [2. Documents and BSON](#2-documents-and-bson)
  * [3. Embedding versus referencing](#3-embedding-versus-referencing)
  * [4. Indexes](#4-indexes)
  * [5. Querying and aggregation](#5-querying-and-aggregation)
  * [6. Transactions and consistency](#6-transactions-and-consistency)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

MongoDB is a document database. Instead of rows in tables, it stores JSON-like BSON documents inside collections, and collections live in a database. Documents in the same collection do not have to share the same fields, so the schema is flexible.

You model data around how you read it, choosing for each relationship whether to embed it inside one document or reference it across documents. Embedding suits data you read and write together; referencing suits data that grows without bound or is shared widely. Push this too far in the relational direction — deep chains of references emulating joins, or arrays that grow forever — and you get slow queries and documents that eventually hit the 16 MB limit.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Databases collections and documents

The database → collection → document hierarchy, `_id`, and schema validation. See [databases-collections-and-documents.md](databases-collections-and-documents.md).

### 2. Documents and BSON

BSON types, the 16 MB document limit, and GridFS. See [documents-and-bson.md](documents-and-bson.md).

### 3. Embedding versus referencing

The central modeling decision: when to embed and when to reference. See [embedding-versus-referencing.md](embedding-versus-referencing.md).

### 4. Indexes

Single-field, compound, multikey, and specialized indexes (text, geo, TTL). See [indexes.md](indexes.md).

### 5. Querying and aggregation

Query filters, projection, the aggregation pipeline, and update operators. See [querying-and-aggregation.md](querying-and-aggregation.md).

### 6. Transactions and consistency

Single-document atomicity, multi-document transactions, and read/write concerns. See [transactions-and-consistency.md](transactions-and-consistency.md).

### 7. Practical rule

```text
Model for your read patterns, not for normalization.
Embed what you read together; reference what grows without bound.
Index for your queries and confirm with explain().
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: design collections around access patterns, not entities
- TODO: keep documents bounded; avoid ever-growing arrays
- TODO: create compound indexes matching query + sort; verify with `explain()`

### Operations and production

- TODO: always run a replica set in production; pick a shard key carefully
- TODO: set read/write concerns for required durability
- TODO: monitor working set vs RAM, slow queries, oplog window

## References

- Official docs: https://www.mongodb.com/docs/
- Related: [databases-collections-and-documents.md](databases-collections-and-documents.md)
