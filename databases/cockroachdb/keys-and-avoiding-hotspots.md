# CockroachDB — keys and avoiding hotspots

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The primary key sets storage order](#1-the-primary-key-sets-storage-order)
  * [2. Why sequential keys hotspot](#2-why-sequential-keys-hotspot)
  * [3. Spreading writes](#3-spreading-writes)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

In CockroachDB the primary key does double duty: it identifies a row and it sets the row's position in the sorted keyspace, which decides where the row physically lives. A sequential key like an auto-incrementing integer therefore sends every new insert to the end of the keyspace and onto a single range and node, creating a write hotspot that no amount of nodes can relieve.

The fix is to spread inserts across ranges, using random UUIDs or hash-sharded indexes so writes land on many nodes at once. Choosing keys for distribution, not just uniqueness, is the central modeling skill here.

---

## Detailed explanation with examples

### 1. The primary key sets storage order

- TODO: PK = clustered order in the keyspace

### 2. Why sequential keys hotspot

- TODO: monotonic keys → one range → one node
- TODO: `SERIAL`/sequence pitfalls

### 3. Spreading writes

- TODO: `gen_random_uuid()` primary keys
- TODO: hash-sharded indexes for ordered access patterns

### 4. Practical rule

```text
Never use a sequential primary key for high-write tables.
Use UUIDs, or hash-shard when you still need ordered scans.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: default to UUID PKs; hash-shard indexes on monotonic columns

### Operations and production

- TODO: watch for hot ranges from accidental sequential keys

## References

- Official docs: https://www.cockroachlabs.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
