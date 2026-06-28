# etcd — clustering and consistency

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Raft and quorum](#1-raft-and-quorum)
  * [2. Linearizable versus serializable reads](#2-linearizable-versus-serializable-reads)
  * [3. Sizing and maintenance](#3-sizing-and-maintenance)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

etcd runs as a small cluster that uses the Raft consensus protocol to keep a strongly consistent, replicated log across its members. Because every write must be agreed by a majority, the cluster is sized as an odd number of members, typically three or five, so it can tolerate the loss of a minority while still forming a quorum.

Reads are linearizable by default, meaning they reflect the latest committed write, with a faster serializable read available when slightly stale data is acceptable. Running etcd well means fast disks for the Raft log, regular compaction and defragmentation, and watching the database size against its quota.

---

## Detailed explanation with examples

### 1. Raft and quorum

- TODO: leader election; majority commit
- TODO: odd member counts (3, 5); failure tolerance

### 2. Linearizable versus serializable reads

- TODO: default linearizable reads
- TODO: serializable reads for lower latency / stale-ok

### 3. Sizing and maintenance

- TODO: fast disks (fsync latency)
- TODO: `--quota-backend-bytes`; defrag; snapshots

### 4. Practical rule

```text
Run 3 or 5 members on fast disks.
Keep DB size under quota: compact + defrag; back up with snapshots.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: use serializable reads only where staleness is acceptable

### Operations and production

- TODO: monitor leader changes, fsync/commit latency, DB size; test snapshot restore

## References

- Official docs: https://etcd.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
