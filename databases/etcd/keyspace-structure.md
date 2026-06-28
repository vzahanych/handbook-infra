# etcd — keyspace structure

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. A flat ordered keyspace](#1-a-flat-ordered-keyspace)
  * [2. Prefixes and range reads](#2-prefixes-and-range-reads)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

etcd stores a single flat, lexicographically ordered set of keys mapping byte strings to byte values, with no tables, collections, or nested buckets. Hierarchy exists only by convention: keys are named with slash-separated prefixes like `/registry/pods/default/`, and you query a whole subtree with a range request over that prefix.

Because the keyspace is ordered, range reads are efficient and are the normal way to list related keys rather than fetching them one by one. This simple model is deliberate, since etcd is built for coordination data, not arbitrary structured storage.

---

## Detailed explanation with examples

### 1. A flat ordered keyspace

- TODO: byte keys/values; lexicographic ordering

### 2. Prefixes and range reads

- TODO: prefix conventions; range queries over a subtree

### 3. Practical rule

```text
Design keys as ordered prefixes; list with range reads, not many gets.
Keep values small.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: structure keys by prefix; avoid large values

### Operations and production

- TODO: avoid huge ranges in a single request

## References

- Official docs: https://etcd.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
