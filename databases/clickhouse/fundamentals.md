# ClickHouse — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Columnar storage](#1-columnar-storage)
  * [2. Tables and engines](#2-tables-and-engines)
  * [3. Primary key and the sparse index](#3-primary-key-and-the-sparse-index)
  * [4. Data skipping indexes and projections](#4-data-skipping-indexes-and-projections)
  * [5. Partitioning and merges](#5-partitioning-and-merges)
  * [6. Materialized views](#6-materialized-views)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

ClickHouse is a column-oriented database for analytics. It stores each column separately and is built to scan and aggregate billions of rows quickly, not to do point updates or single-row lookups. The most important choice when creating a table is the engine, almost always a member of the MergeTree family.

Performance comes from the sorting key and partitioning rather than from traditional indexes. What ClickHouse calls the primary key is really a sparse index over that sort order, and it neither enforces uniqueness nor points at individual rows — it just lets the engine skip large blocks that cannot match. Because storage is built around appending parts and merging them in the background, OLTP-style workloads of frequent small inserts, updates, and deletes work directly against the design; you batch inserts and let merges do the rest.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Columnar storage

Per-column storage, the OLAP focus, and compression. See [columnar-storage.md](columnar-storage.md).

### 2. Tables and engines

The MergeTree family, `ORDER BY`/`PARTITION BY`, and integration engines. See [tables-and-engines.md](tables-and-engines.md).

### 3. Primary key and the sparse index

The sparse, non-unique primary index and why column order matters. See [primary-key-and-the-sparse-index.md](primary-key-and-the-sparse-index.md).

### 4. Data skipping indexes and projections

Skipping indexes and projections for off-axis queries. See [data-skipping-indexes-and-projections.md](data-skipping-indexes-and-projections.md).

### 5. Partitioning and merges

Parts, background merges, partition pruning, TTL, and the small-parts problem. See [partitioning-and-merges.md](partitioning-and-merges.md).

### 6. Materialized views

Insert-triggered views and aggregating rollups. See [materialized-views.md](materialized-views.md).

### 7. Practical rule

```text
Insert in large batches; never row-by-row.
Order by the columns you filter on (low to high cardinality).
Reach for materialized views to pre-aggregate, not for OLTP updates.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: choose `ORDER BY` to match filters; use `LowCardinality` for repetitive strings
- TODO: pick the right MergeTree variant for dedup/rollup needs
- TODO: avoid `Nullable` and tiny inserts on hot paths

### Operations and production

- TODO: batch ingest (or buffer via Kafka engine); watch part counts
- TODO: use partition TTL for retention; monitor merges and disk
- TODO: replication via ReplicatedMergeTree + ClickHouse Keeper/ZooKeeper

## References

- Official docs: https://clickhouse.com/docs
- Related: [tables-and-engines.md](tables-and-engines.md)
