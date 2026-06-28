# Tempo — storage and object backends

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Compressed blocks in object storage](#1-compressed-blocks-in-object-storage)
  * [2. Minimal indexing](#2-minimal-indexing)
  * [3. Retention and compaction](#3-retention-and-compaction)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Like Loki, Tempo keeps the bulk of its data as compressed blocks in object storage such as S3, GCS, or Azure Blob, which is what makes storing large trace volumes inexpensive. Traditionally it built almost no search index, relying on trace-ID lookup, though newer versions add more indexing to support TraceQL search.

Retention is configured by age and enforced by a compactor that also merges blocks. The object-storage design means scaling trace retention is mostly a question of bucket size and cost, not of running a large indexing cluster.

---

## Detailed explanation with examples

### 1. Compressed blocks in object storage

- TODO: S3/GCS/Azure-backed blocks; low cost

### 2. Minimal indexing

- TODO: ID lookup historically; added indexing for TraceQL

### 3. Retention and compaction

- TODO: retention by age; compactor merges blocks

### 4. Practical rule

```text
Back blocks with object storage; retention is mostly a cost/bucket-size decision.
Run the compactor; set retention by age.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: enable the indexing needed for your TraceQL usage

### Operations and production

- TODO: run the compactor; monitor object-store usage and block counts

## References

- Official docs: https://grafana.com/docs/tempo/latest/
- Overview: [fundamentals.md](fundamentals.md)
