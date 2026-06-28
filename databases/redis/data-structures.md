# Redis — data structures

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Strings, lists, hashes](#1-strings-lists-hashes)
  * [2. Sets and sorted sets](#2-sets-and-sorted-sets)
  * [3. Streams](#3-streams)
  * [4. Specialized types](#4-specialized-types)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Redis is often called a key-value store, but the real power is that the value is a typed data structure with its own commands and performance guarantees. Strings hold text, counters, and bitmaps; lists work as queues; hashes model objects; sets enforce uniqueness; and sorted sets keep members ordered by score, which is what makes leaderboards and ranking fast.

Streams add an append-only log with consumer groups for messaging, and specialized types like HyperLogLog and Geo solve counting and location problems. Choosing the structure that matches your operation is the whole art of using Redis well.

---

## Detailed explanation with examples

### 1. Strings, lists, hashes

- TODO: String (`SET`/`GET`/`INCR`, bitmaps), List (`LPUSH`/`RPOP`)
- TODO: Hash (`HSET`/`HGETALL`) for objects

### 2. Sets and sorted sets

- TODO: Set uniqueness/membership
- TODO: Sorted Set scores for ranking/leaderboards

### 3. Streams

- TODO: append-only log; consumer groups

### 4. Specialized types

- TODO: HyperLogLog, Geo, Bitmaps

### 5. Practical rule

```text
Pick the structure that matches the operation (sorted set = ranking, hash = object).
Mind command complexity (avoid O(N) commands on huge keys).
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: choose structures by access pattern; avoid unbounded collections in one key

### Operations and production

- TODO: watch for big keys; prefer streams over lists for reliable queues

## References

- Official docs: https://redis.io/docs/data-types/
- Overview: [fundamentals.md](fundamentals.md)
