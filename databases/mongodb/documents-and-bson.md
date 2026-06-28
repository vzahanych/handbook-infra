# MongoDB — documents and BSON

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. BSON types](#1-bson-types)
  * [2. The 16 MB limit](#2-the-16-mb-limit)
  * [3. GridFS](#3-gridfs)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A MongoDB document looks like JSON but is stored as BSON, a binary format that adds types JSON lacks, such as dates, 64-bit integers, decimals, and binary data. This richer typing matters because it lets the database sort, compare, and index values correctly rather than treating everything as a string or double.

A single document has a hard size limit of 16 MB, a deliberate constraint that pushes very large or unbounded data toward references or GridFS. Thinking in BSON types, not loose JSON, keeps queries and indexes predictable.

---

## Detailed explanation with examples

### 1. BSON types

- TODO: dates, `int`/`long`, `decimal128`, binary, `ObjectId`
- TODO: why type matters for sort/compare/index

### 2. The 16 MB limit

- TODO: per-document hard limit; what to do near it

### 3. GridFS

- TODO: storing large files as chunks

### 4. Practical rule

```text
Use proper BSON types (dates, decimals) — don't store everything as strings.
Keep documents well under 16 MB; use references or GridFS for large blobs.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: store dates as BSON dates, money as `decimal128`

### Operations and production

- TODO: monitor document growth; alert before documents approach the limit

## References

- Official docs: https://www.mongodb.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [embedding-versus-referencing.md](embedding-versus-referencing.md)
