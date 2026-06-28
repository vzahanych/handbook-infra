# Redis — persistence and durability

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. RDB snapshots](#1-rdb-snapshots)
  * [2. AOF append-only file](#2-aof-append-only-file)
  * [3. Choosing a posture](#3-choosing-a-posture)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Although Redis serves everything from memory, it can persist to disk in two ways, and the choice defines how much data a crash can lose. RDB takes point-in-time snapshots, which are compact and fast to load but lose everything written since the last snapshot. AOF, the append-only file, logs every write and replays it on restart, giving much stronger durability at some cost in file size and speed.

The key realization is that durability is not the default posture: you decide whether an instance is a disposable cache, where RDB or even no persistence is fine, or a store of record, where AOF belongs.

---

## Detailed explanation with examples

### 1. RDB snapshots

- TODO: snapshot triggers; compact, fast load, data-loss window

### 2. AOF append-only file

- TODO: `appendfsync` options; rewrite/compaction

### 3. Choosing a posture

- TODO: cache vs store of record
- TODO: RDB + AOF together

### 4. Practical rule

```text
Decide cache vs store of record first.
Cache: RDB (or none) is fine. Store of record: enable AOF.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: do not assume Redis is durable; design caches to tolerate loss

### Operations and production

- TODO: enable AOF for durable data; test restore; add replicas + Sentinel/Cluster

## References

- Official docs: https://redis.io/docs/management/persistence/
- Overview: [fundamentals.md](fundamentals.md)
