# Neo4j — transactions

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. ACID transactions](#1-acid-transactions)
  * [2. Causal clustering](#2-causal-clustering)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Neo4j is fully ACID: every Cypher query runs inside a transaction, so a set of graph changes either all commit or all roll back, keeping the graph consistent. For high availability and read scaling, Neo4j runs in a causal cluster, where writes go to a leader and are replicated to followers that serve reads, with causal consistency guarantees so a client can read its own writes.

Understanding whether an operation is a read or a write determines where it can be routed in such a cluster. The transactional model means you can rely on graph invariants holding even under concurrent access.

---

## Detailed explanation with examples

### 1. ACID transactions

- TODO: query = transaction; commit/rollback; explicit transactions

### 2. Causal clustering

- TODO: leader writes, follower reads; causal consistency (read-your-writes)

### 3. Practical rule

```text
Rely on ACID for graph invariants; batch large writes into sized transactions.
Route reads to followers, writes to the leader in a cluster.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: keep transactions appropriately sized; use bookmarks for read-your-writes

### Operations and production

- TODO: use causal cluster for HA; monitor leader elections and replication lag

## References

- Official docs: https://neo4j.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
