# etcd — transactions

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Compare, then, else](#1-compare-then-else)
  * [2. Compare-and-swap patterns](#2-compare-and-swap-patterns)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

etcd transactions are not multi-statement SQL transactions but a single atomic compare-and-swap operation expressed as compare, then, and else clauses. The transaction first checks conditions — for example that a key is at an expected revision or has a given value — and then applies one set of operations if the comparison holds and another if it does not, all atomically.

This is the building block for safe concurrent updates, because two clients racing to change the same key cannot both succeed; one comparison will fail. Leader election and distributed locks are implemented directly on top of this primitive.

---

## Detailed explanation with examples

### 1. Compare, then, else

- TODO: `Txn().If(...).Then(...).Else(...)`
- TODO: comparing on value, revision, or existence

### 2. Compare-and-swap patterns

- TODO: optimistic updates keyed on mod-revision
- TODO: building locks/election

### 3. Practical rule

```text
Use Txn compare-and-swap for any contested key update.
Compare on mod-revision for safe optimistic writes.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: never blind-write contested keys; gate writes with a compare

### Operations and production

- TODO: keep transactions small; they go through Raft

## References

- Official docs: https://etcd.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
