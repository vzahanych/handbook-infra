# etcd — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Keyspace structure](#1-keyspace-structure)
  * [2. MVCC and revisions](#2-mvcc-and-revisions)
  * [3. Leases and coordination](#3-leases-and-coordination)
  * [4. Transactions](#4-transactions)
  * [5. Clustering and consistency](#5-clustering-and-consistency)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

etcd is a strongly consistent, distributed key-value store built on the Raft consensus protocol. It keeps a flat, ordered set of keys and values, and every change bumps a single global revision number. It is best known as the store behind Kubernetes.

etcd is a coordination layer rather than a general database, so it trades raw throughput for correctness and watchability. That trade-off is what makes its primitives — leases, watches, and compare-and-swap transactions — the right tools for distributed locks, leader election, and service registration. Push bulk-datastore work onto it instead and large values, high write rates, and uncompacted history will quickly exhaust it.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Keyspace structure

The flat, ordered keyspace, prefix conventions, and range reads. See [keyspace-structure.md](keyspace-structure.md).

### 2. MVCC and revisions

The global revision, watches, and compaction. See [mvcc-and-revisions.md](mvcc-and-revisions.md).

### 3. Leases and coordination

Leases for ephemeral keys, distributed locks, and leader election. See [leases-and-coordination.md](leases-and-coordination.md).

### 4. Transactions

The compare/then/else atomic transaction and compare-and-swap. See [transactions.md](transactions.md).

### 5. Clustering and consistency

Raft, quorum sizing, and linearizable vs serializable reads. See [clustering-and-consistency.md](clustering-and-consistency.md).

### 6. Practical rule

```text
Use etcd for coordination and config, not bulk data.
Keep values small, compact regularly, and run an odd quorum.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: structure keys by prefix; use range reads over many small gets
- TODO: use leases for ephemeral state and `Txn` (CAS) for safe updates
- TODO: watch from a known revision; handle compaction errors

### Operations and production

- TODO: 3 or 5 members; fast disks (fsync latency matters)
- TODO: enable auto-compaction and periodic defrag; watch DB size quota
- TODO: back up with snapshots; monitor Raft leader changes and latency

## References

- Official docs: https://etcd.io/docs/
- Related: [../../orchestration/kubernetes/](../../orchestration/kubernetes/)
