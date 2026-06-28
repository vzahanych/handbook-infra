# ClickHouse — partitioning and merges

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Parts and background merges](#1-parts-and-background-merges)
  * [2. Partition pruning and TTL](#2-partition-pruning-and-ttl)
  * [3. The small-parts problem](#3-the-small-parts-problem)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A MergeTree table is physically made of immutable parts, and inserts create new parts that background merges later combine into larger ones. Partitioning, declared with `PARTITION BY`, groups parts into segments — commonly by month — so that queries filtering on the partition expression skip entire segments, and whole partitions can be dropped cheaply for retention.

The merge process is also where engine-specific logic runs, such as deduplication or summing, which is why those results appear only eventually after merges complete. Understanding parts and merges explains why tiny frequent inserts hurt: they create too many parts for the merger to keep up with.

---

## Detailed explanation with examples

### 1. Parts and background merges

- TODO: immutable parts; merges; eventual dedup/sum

### 2. Partition pruning and TTL

- TODO: `PARTITION BY`; dropping partitions; column/row TTL

### 3. The small-parts problem

- TODO: too-many-parts from tiny inserts; batching/buffering

### 4. Practical rule

```text
Insert in big batches; partition coarsely (e.g. by month).
Use partition drop + TTL for retention; avoid tiny frequent inserts.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: keep partition cardinality low; align partitions with retention

### Operations and production

- TODO: monitor part counts and merges; buffer or batch ingest

## References

- Official docs: https://clickhouse.com/docs
- Overview: [fundamentals.md](fundamentals.md)
