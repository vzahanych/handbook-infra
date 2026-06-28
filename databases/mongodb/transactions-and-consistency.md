# MongoDB — transactions and consistency

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Single-document atomicity](#1-single-document-atomicity)
  * [2. Multi-document transactions](#2-multi-document-transactions)
  * [3. Read and write concerns](#3-read-and-write-concerns)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

MongoDB guarantees that a single document update is atomic, which, combined with embedding, means many operations that would need a transaction in a relational design need none here. When you genuinely must change several documents together, multi-document transactions are available on replica sets and sharded clusters with the same all-or-nothing semantics, though they cost more than single-document writes.

Read and write concerns let you tune how many replicas must acknowledge an operation, trading latency for durability and consistency. Designing so that atomicity usually lands within one document keeps the system both simpler and faster.

---

## Detailed explanation with examples

### 1. Single-document atomicity

- TODO: atomic update of one document (incl. embedded data)

### 2. Multi-document transactions

- TODO: replica-set/sharded transactions; cost vs single-doc writes

### 3. Read and write concerns

- TODO: write concern (`w`, `majority`, `j`)
- TODO: read concern and read preference

### 4. Practical rule

```text
Model so atomicity lands in one document; reach for transactions only when needed.
Use `majority` write concern for durability that survives failover.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer single-document atomic updates over multi-doc transactions

### Operations and production

- TODO: set write/read concern per durability need; always run a replica set in prod

## References

- Official docs: https://www.mongodb.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
