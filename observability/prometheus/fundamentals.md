# Prometheus — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The pull model and scraping](#1-the-pull-model-and-scraping)
  * [2. Metric types](#2-metric-types)
  * [3. Labels and the data model](#3-labels-and-the-data-model)
  * [4. PromQL basics](#4-promql-basics)
  * [5. Recording and alerting rules](#5-recording-and-alerting-rules)
  * [6. Storage and retention](#6-storage-and-retention)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Prometheus is a metrics monitoring system built around a pull model and a time-series database. Instead of receiving metrics pushed to it, Prometheus scrapes HTTP endpoints that targets expose, collecting numeric samples at a regular interval and storing them as time series identified by a metric name and a set of labels. This labelled, multi-dimensional model is what makes its query language so powerful.

The query language, PromQL, lets you slice and aggregate those time series by label to answer operational questions, and recording and alerting rules evaluate PromQL continuously to precompute series and fire alerts. Prometheus stores data locally for a bounded retention and favors reliability over long-term durability, so long-term storage is delegated to remote systems. Its pull-based, label-driven design is the mental model everything else builds on.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. The pull model and scraping

How Prometheus scrapes `/metrics` endpoints and discovers targets. See [pull-model-and-scraping.md](pull-model-and-scraping.md).

### 2. Metric types

Counter, gauge, histogram, and summary and when to use each. See [metric-types.md](metric-types.md).

### 3. Labels and the data model

Multi-dimensional series, labels, and cardinality. See [labels-and-the-data-model.md](labels-and-the-data-model.md).

### 4. PromQL basics

Selectors, `rate()`, and aggregation by labels. See [promql-basics.md](promql-basics.md).

### 5. Recording and alerting rules

Precomputed series and alerts that fire to Alertmanager. See [recording-and-alerting-rules.md](recording-and-alerting-rules.md).

### 6. Storage and retention

Local TSDB blocks, retention, and remote-write for long-term. See [storage-and-retention.md](storage-and-retention.md).

### 7. Practical rule

```text
Pull metrics, model them with bounded labels, query with rate() + aggregation.
Keep Prometheus local/short-term; remote-write for long-term and scale.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: choose the right metric type; keep label cardinality bounded
- TODO: use `rate()` on counters; aggregate with `sum by (...)`
- TODO: add `for` durations to alerting rules to avoid flapping

### Operations and production

- TODO: size retention; use remote-write (Thanos/Mimir/Cortex) for long-term/global
- TODO: monitor TSDB head series, scrape failures, and rule evaluation time

## References

- Official docs: https://prometheus.io/docs/
- Related: [../grafana/fundamentals.md](../grafana/fundamentals.md), [../alertmanager/fundamentals.md](../alertmanager/fundamentals.md)
