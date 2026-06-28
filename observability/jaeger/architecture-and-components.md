# Jaeger — architecture and components

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The pipeline](#1-the-pipeline)
  * [2. Collector and query](#2-collector-and-query)
  * [3. The OpenTelemetry Collector](#3-the-opentelemetry-collector)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Jaeger is built from a few cooperating components, though modern versions have streamlined them. Instrumented applications send spans, historically to a per-host agent and then to a collector, which validates, processes, and writes them to storage; the query service reads from storage to serve the UI.

In current Jaeger and with OpenTelemetry, the agent is largely replaced by the OpenTelemetry Collector, simplifying the pipeline to collector, storage, and query. Knowing the receive-process-store-query flow is what lets you reason about where traces can be lost or delayed.

---

## Detailed explanation with examples

### 1. The pipeline

- TODO: app → (agent) → collector → storage → query → UI

### 2. Collector and query

- TODO: collector processes/writes; query serves the UI

### 3. The OpenTelemetry Collector

- TODO: OTel Collector replacing the legacy agent

### 4. Practical rule

```text
Think receive → process → store → query.
Prefer the OpenTelemetry Collector over the legacy agent.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: send via the OTel Collector; avoid deprecated agent paths

### Operations and production

- TODO: scale collectors with span volume; monitor each stage for drops

## References

- Official docs: https://www.jaegertracing.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
