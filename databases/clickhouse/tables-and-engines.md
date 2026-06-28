# ClickHouse — tables and engines

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The MergeTree family](#1-the-mergetree-family)
  * [2. ORDER BY and PARTITION BY](#2-order-by-and-partition-by)
  * [3. Integration engines](#3-integration-engines)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

In ClickHouse the table engine is the most consequential part of a table definition, because it decides how data is stored, merged, and queried. The MergeTree family is the workhorse: plain MergeTree for raw event data, ReplacingMergeTree to deduplicate by key, SummingMergeTree and AggregatingMergeTree to roll up metrics as data merges.

Every MergeTree table is defined by its `ORDER BY` sorting key and an optional `PARTITION BY`, which together drive both storage layout and query pruning. Other engines integrate with external systems like Kafka, MySQL, and S3, turning ClickHouse into a query layer over them.

---

## Detailed explanation with examples

### 1. The MergeTree family

- TODO: MergeTree, ReplacingMergeTree, SummingMergeTree, AggregatingMergeTree
- TODO: ReplicatedMergeTree for HA

### 2. ORDER BY and PARTITION BY

- TODO: `ENGINE = MergeTree() ORDER BY ... PARTITION BY ...`
- TODO: data types (`LowCardinality`, `Nullable`, `Array`, `Tuple`)

### 3. Integration engines

- TODO: Kafka, MySQL, PostgreSQL, S3 engines

### 4. Practical rule

```text
Pick the MergeTree variant for your dedup/rollup needs.
Always set a sensible ORDER BY; partition coarsely (often by month).
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: choose engine by semantics; avoid `Nullable` on hot columns

### Operations and production

- TODO: use ReplicatedMergeTree + Keeper for HA; ingest Kafka via the Kafka engine + MV

## References

- Official docs: https://clickhouse.com/docs/en/engines/table-engines/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [primary-key-and-the-sparse-index.md](primary-key-and-the-sparse-index.md)
