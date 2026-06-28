# Cassandra — writes and LSM storage

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The write path](#1-the-write-path)
  * [2. Compaction strategies](#2-compaction-strategies)
  * [3. Tombstones and deletes](#3-tombstones-and-deletes)
  * [4. Reads and read repair](#4-reads-and-read-repair)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Cassandra is built for fast writes, and its storage engine is a log-structured merge tree that never updates data in place. A write is appended to the commit log and held in an in-memory memtable, which is later flushed to an immutable on-disk file called an SSTable.

Because SSTables are never modified, several versions of a row can exist across files, and background compaction merges them and reclaims space. Deletes fit this append-only world by writing a marker called a tombstone rather than removing data, which is why heavy delete or overwrite workloads need attention: too many tombstones slow reads until compaction finally clears them.

---

## Detailed explanation with examples

### 1. The write path

- TODO: commit log → memtable → flush → SSTable
- TODO: why writes are cheap and append-only
- TODO: durability and `commitlog_sync`

### 2. Compaction strategies

- TODO: SizeTiered (STCS), Leveled (LCS), TimeWindow (TWCS)
- TODO: matching strategy to workload (write-heavy, read-heavy, time series)
- TODO: compaction throughput and space amplification

### 3. Tombstones and deletes

- TODO: tombstones as delete markers
- TODO: `gc_grace_seconds` and why deletes are not immediate
- TODO: tombstone build-up and read failures

### 4. Reads and read repair

- TODO: merging row versions across SSTables on read
- TODO: bloom filters, key/partition caches
- TODO: read repair pulling replicas into sync

### 5. Practical rule

```text
Writes are cheap; deletes and overwrites are not — they leave tombstones.
Pick the compaction strategy for the workload (TWCS for time series).
Watch tombstones and pending compactions on read-heavy tables.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: avoid delete-heavy and frequently-overwritten models
- TODO: use TTLs deliberately; prefer TWCS for expiring time-series data

### Operations and production

- TODO: choose compaction per table; monitor pending compactions and SSTable counts
- TODO: alert on tombstone thresholds; tune `gc_grace_seconds` vs repair cadence

## References

- Official docs: https://cassandra.apache.org/doc/
- Overview: [fundamentals.md](fundamentals.md)
