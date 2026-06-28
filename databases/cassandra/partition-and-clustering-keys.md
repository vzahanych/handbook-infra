# Cassandra — partition and clustering keys

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The partition key chooses the node](#1-the-partition-key-chooses-the-node)
  * [2. Clustering columns set the order](#2-clustering-columns-set-the-order)
  * [3. Composite partition keys](#3-composite-partition-keys)
  * [4. Keeping partitions bounded](#4-keeping-partitions-bounded)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

The primary key splits into two jobs, and keeping them straight is most of Cassandra data modeling. The partition key is hashed to decide which nodes hold a row, so it controls distribution and is the value you must supply to read efficiently. The clustering columns then order rows within a single partition, which is what makes range scans like "the latest messages in this chat" fast.

The balance to strike is partition size. A key that groups too much data builds unbounded partitions that overload a node, while one that groups too little scatters related rows and forces many small cross-node reads. Good modeling picks a partition key that is both query-aligned and naturally bounded.

---

## Detailed explanation with examples

### 1. The partition key chooses the node

- TODO: hashing the partition key to a token
- TODO: why every efficient read names the partition key
- TODO: hotspots from low-cardinality or skewed keys

### 2. Clustering columns set the order

- TODO: `WITH CLUSTERING ORDER BY`
- TODO: range queries within a partition
- TODO: ordering and pagination

### 3. Composite partition keys

- TODO: `PRIMARY KEY ((a, b), c)`
- TODO: when to combine columns into the partition key
- TODO: bucketing time series by day/hour

### 4. Keeping partitions bounded

- TODO: rule-of-thumb size limits (rows and bytes)
- TODO: time-bucketing and sharding strategies
- TODO: detecting large partitions (`nodetool tablehistograms`)

### 5. Practical rule

```text
Partition key = distribution + the value you query by.
Clustering columns = sort order inside the partition.
Keep partitions bounded: bucket time series, shard hot keys.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: choose partition keys that spread load and stay bounded
- TODO: bucket high-volume time series (e.g. by day) to cap partition size
- TODO: order clustering columns to match read + pagination needs

### Operations and production

- TODO: monitor partition sizes; alert on large partitions
- TODO: reshard or re-bucket before partitions grow unbounded

## References

- Official docs: https://cassandra.apache.org/doc/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [tables-and-the-primary-key.md](tables-and-the-primary-key.md)
