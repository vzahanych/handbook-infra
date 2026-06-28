# ScyllaDB — partition and clustering keys

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Partition key chooses node and shard](#1-partition-key-chooses-node-and-shard)
  * [2. Clustering columns set the order](#2-clustering-columns-set-the-order)
  * [3. Keeping partitions bounded](#3-keeping-partitions-bounded)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

The partition key and clustering columns play the same two roles as in Cassandra, but with shard-per-core the partition key's choice matters even more for balance. The partition key is hashed to place data on a node and a specific core, so a skewed or low-cardinality key can overload a single core even if the cluster as a whole looks healthy.

Clustering columns order rows inside a partition, enabling efficient range scans. Keeping partitions bounded and well-distributed is therefore the key to spreading load evenly across every core.

---

## Detailed explanation with examples

### 1. Partition key chooses node and shard

- TODO: hashing to token → node → shard
- TODO: hot shards from skewed keys

### 2. Clustering columns set the order

- TODO: `CLUSTERING ORDER BY`; in-partition range scans

### 3. Keeping partitions bounded

- TODO: time-bucketing; size limits; detecting large partitions

### 4. Practical rule

```text
Partition key = distribution across nodes and cores; keep it high-cardinality.
Bucket/shard to keep partitions bounded and cores balanced.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: choose partition keys that spread across shards and stay bounded

### Operations and production

- TODO: monitor per-shard load and large partitions

## References

- Official docs: https://docs.scylladb.com/
- Overview: [fundamentals.md](fundamentals.md)
