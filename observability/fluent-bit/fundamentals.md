# Fluent Bit — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Pipeline: inputs, filters, outputs](#1-pipeline-inputs-filters-outputs)
  * [2. Parsers](#2-parsers)
  * [3. Buffering and backpressure](#3-buffering-and-backpressure)
  * [4. Routing with tags and matches](#4-routing-with-tags-and-matches)
  * [5. Fluent Bit versus Fluentd](#5-fluent-bit-versus-fluentd)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Fluent Bit is a lightweight, high-performance telemetry agent written in C for collecting, processing, and forwarding logs and metrics. It runs as a small-footprint daemon — common as a per-node log collector in Kubernetes — reading from sources, transforming records in a pipeline, and shipping them to destinations like Elasticsearch, Loki, Kafka, or a Fluentd aggregator. Its low resource use is why it has largely displaced heavier agents at the edge.

Its model is a pipeline of inputs, parsers, filters, and outputs, where every record carries a tag that routing rules match to decide where it goes. Buffering and backpressure handling let it absorb spikes and survive downstream outages. Understanding the tagged-record pipeline is the key to configuring it.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Pipeline: inputs, filters, outputs

The four-stage pipeline from source to destination. See [pipeline-inputs-filters-outputs.md](pipeline-inputs-filters-outputs.md).

### 2. Parsers

Turning raw log lines into structured fields. See [parsers.md](parsers.md).

### 3. Buffering and backpressure

Memory vs filesystem buffering and surviving outages. See [buffering-and-backpressure.md](buffering-and-backpressure.md).

### 4. Routing with tags and matches

Tag-based routing and match patterns. See [routing-with-tags-and-matches.md](routing-with-tags-and-matches.md).

### 5. Fluent Bit versus Fluentd

When to use the lightweight agent versus the heavier aggregator. See [fluent-bit-versus-fluentd.md](fluent-bit-versus-fluentd.md).

### 6. Practical rule

```text
Pipeline = input → parse → filter → output, routed by tag/match.
Parse early; enable filesystem buffering for reliability at the edge.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: parse to structured fields early; design a clear tagging scheme
- TODO: route with explicit match patterns; keep filters minimal and fast

### Operations and production

- TODO: enable filesystem buffering + limits to survive outages without OOM
- TODO: monitor retries, dropped records, and buffer usage

## References

- Official docs: https://docs.fluentbit.io/
- Related: [fluent-bit-versus-fluentd.md](fluent-bit-versus-fluentd.md), [../fluentd/fundamentals.md](../fluentd/fundamentals.md)
