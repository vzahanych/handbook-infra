# Redis — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Keyspace and logical databases](#1-keyspace-and-logical-databases)
  * [2. Data structures](#2-data-structures)
  * [3. Expiration and eviction](#3-expiration-and-eviction)
  * [4. Persistence and durability](#4-persistence-and-durability)
  * [5. Atomicity and transactions](#5-atomicity-and-transactions)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Redis is an in-memory key-value store. Every piece of data has a key, but the value is not just a string — it can be a list, a hash, a set, a sorted set, a stream, and more, each with its own commands. Because everything lives in memory, Redis is extremely fast.

You pick the value's data structure to match the operation you need, so a leaderboard becomes a sorted set and a session becomes a hash, each with commands whose cost you can reason about. What you cannot take for granted is durability. Redis lives in memory first, so a crash loses whatever was not captured by an RDB snapshot or the append-only log — which makes the cache-versus-store-of-record decision something you must make on purpose.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Keyspace and logical databases

The flat keyspace, naming conventions, numbered DBs, and SCAN vs KEYS. See [keyspace-and-logical-databases.md](keyspace-and-logical-databases.md).

### 2. Data structures

Strings, lists, hashes, sets, sorted sets, streams, and specialized types. See [data-structures.md](data-structures.md).

### 3. Expiration and eviction

Per-key TTLs, `maxmemory`, and eviction policies. See [expiration-and-eviction.md](expiration-and-eviction.md).

### 4. Persistence and durability

RDB snapshots, the AOF log, and choosing a durability posture. See [persistence-and-durability.md](persistence-and-durability.md).

### 5. Atomicity and transactions

Single-command atomicity, MULTI/EXEC/WATCH, and Lua scripting. See [atomicity-and-transactions.md](atomicity-and-transactions.md).

### 6. Practical rule

```text
Pick the data structure that matches the operation.
Decide explicitly: cache (RDB ok) or store of record (AOF).
Use SCAN, never KEYS, in production.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: choose structures by access pattern (sorted set for ranking, hash for objects)
- TODO: namespace keys; always set TTLs on cache entries
- TODO: prefer atomic commands / Lua over read-modify-write races

### Operations and production

- TODO: set `maxmemory` + an eviction policy; never `KEYS` on prod
- TODO: choose persistence (RDB/AOF) per durability need; replication + Sentinel/Cluster
- TODO: monitor memory, evictions, latency spikes, big keys

## References

- Official docs: https://redis.io/docs/
- Related: [../../message-brokers/redis-streams/](../../message-brokers/redis-streams/)
