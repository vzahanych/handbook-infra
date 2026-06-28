# CockroachDB — indexes

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Secondary indexes are ranges too](#1-secondary-indexes-are-ranges-too)
  * [2. STORING and covering reads](#2-storing-and-covering-reads)
  * [3. Inverted and partial indexes](#3-inverted-and-partial-indexes)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Secondary indexes in CockroachDB are themselves ranges, replicated and distributed like table data, and they let you query by columns other than the primary key. You can make them composite, partial, or inverted for JSONB and spatial data, and the `STORING` clause adds extra columns so a read can be answered from the index alone without fetching the row.

Because an index is distributed, the same hotspot rules apply, so an index on a sequential column can become a write bottleneck. `EXPLAIN` shows which index a query uses and whether it stays index-only.

---

## Detailed explanation with examples

### 1. Secondary indexes are ranges too

- TODO: distributed indexes; hotspot rules apply to indexes

### 2. STORING and covering reads

- TODO: `STORING (...)` for index-only scans

### 3. Inverted and partial indexes

- TODO: inverted indexes (JSONB, arrays, spatial)
- TODO: partial indexes

### 4. Practical rule

```text
Use STORING to make hot reads index-only.
Avoid indexing monotonic columns directly; hash-shard if needed.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: cover read-hot queries; verify with `EXPLAIN`/`EXPLAIN ANALYZE`

### Operations and production

- TODO: watch index write amplification and hot index ranges

## References

- Official docs: https://www.cockroachlabs.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
