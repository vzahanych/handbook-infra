# TimescaleDB — hypertables and chunks

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Creating a hypertable](#1-creating-a-hypertable)
  * [2. Chunks and the time interval](#2-chunks-and-the-time-interval)
  * [3. Space partitioning](#3-space-partitioning)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

The central abstraction is the hypertable: a single logical table that TimescaleDB automatically partitions into many physical child tables called chunks, each holding a slice of time. You create a normal table and call `create_hypertable()` on it, after which inserts and queries behave as if it were one table while the extension routes them to the right chunks behind the scenes.

Because recent data lives in its own small chunks, inserts of new rows and queries over a time window touch only a few chunks instead of the whole dataset. Choosing the chunk time interval — large enough to limit chunk count, small enough that active chunks fit in memory — is the main sizing decision.

---

## Detailed explanation with examples

### 1. Creating a hypertable

- TODO: regular table → `create_hypertable('t', 'time')`
- TODO: transparent inserts/queries across chunks

### 2. Chunks and the time interval

- TODO: `chunk_time_interval` sizing guidance
- TODO: active chunks fitting in memory

### 3. Space partitioning

- TODO: optional space dimension (e.g. device_id)

### 4. Practical rule

```text
Size chunk_time_interval so active chunks fit in memory.
Let the hypertable route inserts/queries; query across chunks normally.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: pick the time column carefully; add space partitioning only when needed

### Operations and production

- TODO: monitor chunk count; re-tune interval as ingest changes

## References

- Official docs: https://docs.tigerdata.com/
- Overview: [fundamentals.md](fundamentals.md)
