# Elasticsearch — sharding and scaling

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Shard count and size](#1-shard-count-and-size)
  * [2. Replicas](#2-replicas)
  * [3. Index lifecycle management](#3-index-lifecycle-management)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Scaling Elasticsearch is largely the discipline of getting shard count and size right, because every shard carries fixed overhead and an oversharded cluster wastes heap and slows everything down. The usual guidance is to keep each shard in the tens of gigabytes and avoid creating far more shards than nodes can comfortably hold.

Replicas add high availability and increase read throughput, since searches can run on either primaries or replicas, at the cost of extra storage. For time-series data, index lifecycle management automates rolling over to new indices, moving older ones to cheaper storage, and eventually deleting them, which keeps shard counts under control as data grows.

---

## Detailed explanation with examples

### 1. Shard count and size

- TODO: per-shard overhead; tens of GB target; oversharding

### 2. Replicas

- TODO: HA + read throughput; storage cost

### 3. Index lifecycle management

- TODO: ILM hot/warm/cold/delete phases; rollover

### 4. Practical rule

```text
Keep shards in the tens of GB; don't create far more shards than nodes.
Use ILM + rollover for time-series so shard counts stay bounded.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: size indices/shards to data volume; use rollover for growing data

### Operations and production

- TODO: configure ILM phases; monitor heap, GC, cluster health (green/yellow/red)

## References

- Official docs: https://www.elastic.co/guide/
- Overview: [fundamentals.md](fundamentals.md)
