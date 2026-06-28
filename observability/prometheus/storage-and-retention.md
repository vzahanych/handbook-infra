# Prometheus — storage and retention

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The local TSDB](#1-the-local-tsdb)
  * [2. Retention](#2-retention)
  * [3. Remote write for long-term](#3-remote-write-for-long-term)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Prometheus stores scraped samples in a local time-series database on disk, organized into compacted blocks, and keeps them for a configured retention period measured in time or size. This local storage is optimized for fast recent queries and is deliberately not a long-term or highly-durable store — a single Prometheus is a single node.

For long retention, global views, or durability, Prometheus writes through a remote-write interface to systems like Thanos, Cortex, or Mimir that handle long-term storage and horizontal scale. Understanding that local storage is bounded and node-local explains why remote storage exists.

---

## Detailed explanation with examples

### 1. The local TSDB

- TODO: head block + compacted blocks; WAL

### 2. Retention

- TODO: `--storage.tsdb.retention.time/size`

### 3. Remote write for long-term

- TODO: remote_write to Thanos/Mimir/Cortex; global query

### 4. Practical rule

```text
Treat local storage as short-term and node-local.
Remote-write to Thanos/Mimir/Cortex for long-term, durable, global views.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: set retention to match local-query needs only

### Operations and production

- TODO: provision disk for head + blocks; use remote-write for HA/long-term; back up if needed

## References

- Official docs: https://prometheus.io/docs/prometheus/latest/storage/
- Overview: [fundamentals.md](fundamentals.md)
