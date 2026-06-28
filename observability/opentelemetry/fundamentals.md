# OpenTelemetry — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Signals: traces, metrics, logs](#1-signals-traces-metrics-logs)
  * [2. Instrumentation and SDKs](#2-instrumentation-and-sdks)
  * [3. Context propagation](#3-context-propagation)
  * [4. The Collector](#4-the-collector)
  * [5. Exporters and OTLP](#5-exporters-and-otlp)
  * [6. Semantic conventions](#6-semantic-conventions)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

OpenTelemetry (OTel) is a vendor-neutral standard and toolkit for generating and shipping telemetry — traces, metrics, and logs — so you instrument your code once and send the data anywhere. Instead of each backend having its own SDK and format, OTel provides language SDKs, a wire protocol called OTLP, and the Collector, decoupling how you produce telemetry from where you store it. This is why it has become the default way to instrument modern systems.

The pieces fit together as: SDKs in your application produce the three signals and propagate context across services; an optional Collector receives, processes, and exports that data; and exporters using OTLP send it to backends like Prometheus, Tempo, Jaeger, or Loki. Semantic conventions standardize attribute names so data is consistent across languages and tools. OTel is the producer side that the other observability backends consume.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Signals: traces, metrics, logs

The three correlated signals under one API and data model. See [signals-traces-metrics-logs.md](signals-traces-metrics-logs.md).

### 2. Instrumentation and SDKs

Automatic and manual instrumentation via language SDKs. See [instrumentation-and-sdks.md](instrumentation-and-sdks.md).

### 3. Context propagation

Carrying trace context across services (W3C Trace Context). See [context-propagation.md](context-propagation.md).

### 4. The Collector

Receiver → processor → exporter pipeline as a standalone service. See [the-collector.md](the-collector.md).

### 5. Exporters and OTLP

OTLP as the native protocol and exporters to backends. See [exporters-and-otlp.md](exporters-and-otlp.md).

### 6. Semantic conventions

Standard attribute names for portable, queryable telemetry. See [semantic-conventions.md](semantic-conventions.md).

### 7. Practical rule

```text
Instrument once with OTel; export OTLP to a Collector; send anywhere.
Follow semantic conventions and propagate context everywhere.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: auto-instrument for breadth, manual-instrument the domain spans that matter
- TODO: follow semantic conventions; propagate W3C Trace Context across all hops

### Operations and production

- TODO: run a Collector so apps speak OTLP to one place; centralize sampling/processing
- TODO: standardize on OTLP so backends can change without re-instrumenting

## References

- Official docs: https://opentelemetry.io/docs/
- Related: [../tempo/fundamentals.md](../tempo/fundamentals.md), [../jaeger/fundamentals.md](../jaeger/fundamentals.md)
