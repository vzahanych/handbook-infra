# Redis — expiration and eviction

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Per-key TTL](#1-per-key-ttl)
  * [2. maxmemory and eviction policies](#2-maxmemory-and-eviction-policies)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Redis lets any key carry a time to live, after which the key is automatically removed, which is what makes it a natural cache. You set expiry with `EXPIRE` or at write time, check it with `TTL`, and cancel it with `PERSIST`.

Separately, when memory fills up to the configured `maxmemory`, Redis applies an eviction policy to decide what to drop, with options like least-recently-used across all keys or only among keys that already have a TTL. Setting both a memory limit and a deliberate eviction policy is essential, because the default can refuse writes once memory is exhausted.

---

## Detailed explanation with examples

### 1. Per-key TTL

- TODO: `EXPIRE`, `SET ... EX`, `TTL`, `PERSIST`

### 2. maxmemory and eviction policies

- TODO: `maxmemory` setting
- TODO: `allkeys-lru`, `volatile-lru`, `allkeys-lfu`, `noeviction`

### 3. Practical rule

```text
Always set TTLs on cache keys.
Set maxmemory plus an explicit eviction policy — don't rely on the default.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: give cache entries TTLs; avoid immortal keys that grow forever

### Operations and production

- TODO: set `maxmemory` + policy; alert on eviction rate and memory pressure

## References

- Official docs: https://redis.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
