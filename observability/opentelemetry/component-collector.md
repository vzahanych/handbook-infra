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

The OpenTelemetry Collector is a standalone service that sits between your applications and your observability backends. Its job is to receive telemetry, process it, and export it onward, which lets your applications stay simple and unaware of where their data ultimately goes. You describe everything it does in configuration rather than code, and it is built as a pipeline with three stages.

The first stage is receivers. A receiver is an entry point that accepts incoming telemetry in some format, whether that is the native OpenTelemetry Protocol or an older format such as Jaeger or Prometheus. A single collector can run many receivers at once, so it can act as a common landing point for data arriving in different shapes.

The second stage is processors. A processor transforms the data as it passes through, and this is where most of the useful work happens. Processors batch records together for efficiency, filter out noise, redact sensitive fields, enrich data with extra attributes, and apply tail sampling once a full trace has been seen.

The third stage is exporters. An exporter takes the processed data and sends it to a destination, which might be one backend or several at the same time. Because the collector can fan the same data out to multiple exporters, you can send traces to one system and metrics to another, or try a new backend in parallel without touching your applications.

Running a collector is the recommended pattern for exactly these reasons. Your applications only ever speak one protocol to one place, while the collector absorbs the complexity of sampling, formatting, and routing. The result is simpler instrumentation and a single point where telemetry policy lives, typically deployed as a lightweight agent next to each workload feeding a larger central gateway.

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
