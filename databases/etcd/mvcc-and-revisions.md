# etcd — MVCC and revisions

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The global revision](#1-the-global-revision)
  * [2. Watches](#2-watches)
  * [3. Compaction](#3-compaction)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

etcd is multiversion: every change to the store increments a single global revision number, and old versions of keys are kept until they are compacted away. This means you can read not just the current value of a key but its value as of a past revision, and each key also tracks when it was created, last modified, and how many times.

Watches build on this, letting a client stream every change that happens after a given revision, which is how Kubernetes controllers react to state changes. The cost of keeping history is space, so etcd must be compacted regularly and occasionally defragmented to reclaim disk.

---

## Detailed explanation with examples

### 1. The global revision

- TODO: monotonic revision; create/mod/version per key
- TODO: reading historical revisions

### 2. Watches

- TODO: watching from a revision; change streams

### 3. Compaction

- TODO: `--auto-compaction`; reclaiming history; defrag

### 4. Practical rule

```text
Watch from a known revision and handle "compacted" errors.
Compact regularly; defrag to reclaim space.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: track the last seen revision in clients; resume watches from it

### Operations and production

- TODO: enable auto-compaction; schedule defrag; monitor DB size

## References

- Official docs: https://etcd.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
