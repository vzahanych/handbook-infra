# Redis — keyspace and logical databases

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. A flat keyspace](#1-a-flat-keyspace)
  * [2. Numbered logical databases](#2-numbered-logical-databases)
  * [3. SCAN versus KEYS](#3-scan-versus-keys)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Redis is a single flat keyspace: every value, whatever its structure, is found by one binary-safe key, and there is no nesting of keys into tables or collections. Because the namespace is flat, teams impose structure through naming conventions, using colon-separated prefixes like `user:1000:sessions` to group related keys.

A server also offers numbered logical databases you can `SELECT` between, but these share the same process and memory and are generally discouraged in favor of separate instances. To inspect keys you use `SCAN`, which iterates incrementally, never `KEYS`, which blocks the server while it walks everything.

---

## Detailed explanation with examples

### 1. A flat keyspace

- TODO: binary-safe keys; prefix naming conventions

### 2. Numbered logical databases

- TODO: `SELECT n`; why separate instances are usually better

### 3. SCAN versus KEYS

- TODO: `SCAN` cursor iteration; never `KEYS` in production

### 4. Practical rule

```text
Namespace keys with prefixes; prefer separate instances over numbered DBs.
Use SCAN, never KEYS, in production.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: consistent key naming scheme; avoid giant single keys

### Operations and production

- TODO: ban `KEYS` in app code; use `SCAN` for maintenance

## References

- Official docs: https://redis.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
