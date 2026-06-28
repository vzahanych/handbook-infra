# OpenTelemetry — the Collector

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Receivers, processors, exporters](#1-receivers-processors-exporters)
  * [2. Deployment patterns](#2-deployment-patterns)
  * [3. Centralized policy](#3-centralized-policy)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

The OpenTelemetry Collector is a standalone service that receives, processes, and exports telemetry, decoupling applications from backends. It is built as a pipeline of receivers that accept data in various formats, processors that batch, filter, sample, and enrich it, and exporters that send it onward, all configured declaratively.

Running a Collector means applications only need to speak OTLP to one place, while the Collector handles fan-out, sampling, and backend-specific formats. It is the recommended deployment pattern because it keeps instrumentation simple and centralizes telemetry policy.

---

## Detailed explanation with examples

### 1. Receivers, processors, exporters

- TODO: pipeline config; batch/filter/sample/attributes processors

### 2. Deployment patterns

- TODO: agent (per-host/sidecar) vs gateway (central)

### 3. Centralized policy

- TODO: sampling, redaction, routing handled centrally

### 4. Practical rule

```text
Send OTLP to a Collector; let it batch, sample, enrich, and fan out.
Apps shouldn't know about backends — the Collector does.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep app exporters pointed at the Collector, not backends directly

### Operations and production

- TODO: run agent + gateway tiers; size batching/queues; monitor Collector drops

## References

- Official docs: https://opentelemetry.io/docs/collector/
- Overview: [fundamentals.md](fundamentals.md)
