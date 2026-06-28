# OpenSearch — sharding and scaling

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Shard count and size](#1-shard-count-and-size)
  * [2. Replicas](#2-replicas)
  * [3. Index State Management](#3-index-state-management)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Scaling OpenSearch follows the Elasticsearch playbook: keep shards reasonably sized in the tens of gigabytes, avoid oversharding, and use replicas for high availability and read throughput. The lifecycle automation has a different name — Index State Management, or ISM, rather than Elasticsearch's ILM — but it serves the same purpose of rolling over, transitioning, and deleting time-series indices by age.

Cluster health is reported with the same green/yellow/red model. The scaling concepts transfer; mainly the management API names change.

---

## Detailed explanation with examples

### 1. Shard count and size

- TODO: per-shard overhead; tens of GB target; oversharding

### 2. Replicas

- TODO: HA + read throughput; storage cost

### 3. Index State Management

- TODO: ISM policies; rollover and transitions (ISM, not ILM)

### 4. Practical rule

```text
Keep shards in the tens of GB; don't oversard.
Use ISM (the OpenSearch name) + rollover for time-series.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: size indices/shards to data volume; rollover for growing data

### Operations and production

- TODO: configure ISM policies; monitor heap, GC, cluster health

## References

- Official docs: https://opensearch.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
