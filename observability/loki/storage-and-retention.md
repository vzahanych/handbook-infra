# Loki — storage and retention

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Index plus chunks](#1-index-plus-chunks)
  * [2. Object storage](#2-object-storage)
  * [3. Retention and multi-tenancy](#3-retention-and-multi-tenancy)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Loki stores data in two parts that reflect its design: a small index of labels and stream metadata, and the much larger compressed log chunks, both kept in object storage like S3 in modern deployments. This object-storage backing is what makes long retention cheap, and retention is configured by period, optionally per-tenant or per-stream.

Loki is multi-tenant and horizontally scalable, splitting work across components for ingestion, querying, and compaction. Understanding that the bulk of data is cheap object-stored chunks explains both its low cost and its reliance on good labels for query speed.

---

## Detailed explanation with examples

### 1. Index plus chunks

- TODO: small label index + large compressed chunks

### 2. Object storage

- TODO: S3/GCS-backed chunks; cheap long retention

### 3. Retention and multi-tenancy

- TODO: retention periods; per-tenant limits; compaction

### 4. Practical rule

```text
Back chunks with object storage; set retention by tenant/stream.
Cost is low because content is just compressed chunks, not an index.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: set per-tenant retention/limits to match needs

### Operations and production

- TODO: run the compactor; monitor object-store usage and query-path components

## References

- Official docs: https://grafana.com/docs/loki/latest/operations/storage/
- Overview: [fundamentals.md](fundamentals.md)
