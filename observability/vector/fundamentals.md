# Vector — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Sources, transforms, sinks](#1-sources-transforms-sinks)
  * [2. The event model](#2-the-event-model)
  * [3. VRL, the Vector Remap Language](#3-vrl-the-vector-remap-language)
  * [4. Buffering and delivery](#4-buffering-and-delivery)
  * [5. Topology and deployment roles](#5-topology-and-deployment-roles)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Vector is a high-performance observability data pipeline, written in Rust, for collecting, transforming, and routing logs, metrics, and traces. Like Fluent Bit and Fluentd it sits between sources and destinations, but it is built as a single fast tool that handles all signal types and emphasizes a powerful transformation language. It is vendor-neutral, shipping data to many backends, and is often used to unify and reshape telemetry before storage.

Its model is a directed graph of components: sources ingest data, transforms reshape and filter it, and sinks send it onward, wired together by naming each component's inputs. The transformation layer, VRL, is its standout feature, and built-in buffering with end-to-end acknowledgements gives reliable delivery. Thinking in a source-transform-sink graph is the key to Vector.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Sources, transforms, sinks

The component graph wired by naming each component's inputs. See [sources-transforms-sinks.md](sources-transforms-sinks.md).

### 2. The event model

Logs, metrics, and traces as typed first-class events. See [the-event-model.md](the-event-model.md).

### 3. VRL, the Vector Remap Language

The compiled expression language for transforming events. See [vrl-the-vector-remap-language.md](vrl-the-vector-remap-language.md).

### 4. Buffering and delivery

Disk/memory buffers and end-to-end acknowledgements. See [buffering-and-delivery.md](buffering-and-delivery.md).

### 5. Topology and deployment roles

Agent versus aggregator deployment. See [topology-and-deployment-roles.md](topology-and-deployment-roles.md).

### 6. Practical rule

```text
Build a source → transform → sink graph; reshape with VRL.
Use disk buffers + acknowledgements for at-least-once delivery.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: model the pipeline as an explicit graph; do reshaping in VRL `remap`
- TODO: treat metrics as first-class events, not just log text

### Operations and production

- TODO: enable disk buffers + end-to-end acks on critical sinks
- TODO: run agent + aggregator tiers; monitor component errors and buffer usage

## References

- Official docs: https://vector.dev/docs/
- Related: [../fluent-bit/fundamentals.md](../fluent-bit/fundamentals.md), [../fluentd/fundamentals.md](../fluentd/fundamentals.md)
