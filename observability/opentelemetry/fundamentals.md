# OpenTelemetry — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Signals](#1-signals)
  * [2. Instrumentation and SDKs](#2-instrumentation-and-sdks)
  * [3. Context propagation](#3-context-propagation)
  * [4. The Collector](#4-the-collector)
  * [5. Exporters and OTLP](#5-exporters-and-otlp)
  * [6. Semantic conventions](#6-semantic-conventions)
  * [7. Resources, scope, and sampling](#7-resources-scope-and-sampling)
  * [8. Practical rule](#8-practical-rule)
* [Components](#components)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

OpenTelemetry, usually shortened to OTel, is a vendor-neutral standard and toolkit for producing and shipping telemetry. The promise is simple: you instrument your code once, and you can send the resulting data to any observability backend you like. It has become the default way to instrument modern systems because it separates the act of producing telemetry from the choice of where that telemetry is stored.

The problem it solves is fragmentation. Before OTel, each monitoring vendor shipped its own agent, its own libraries, and its own data format, so switching backends meant re-instrumenting every service. OpenTelemetry replaces that with one set of language libraries, one wire protocol, and one collector, so the backend becomes a configuration choice rather than a rewrite.

The data itself comes in categories called signals. The four supported today are traces, which follow a request as it moves through your system; metrics, which are numeric measurements taken over time; logs, which are timestamped records of events; and baggage, which carries small pieces of contextual data alongside a request. Two more signals, events and profiles, are still being developed.

The moving parts fit together as a pipeline. Libraries inside your application generate the signals and pass context from one service to the next. An optional collector then receives that data, processes it, and forwards it on. Finally, exporters speaking the OpenTelemetry Protocol, known as OTLP, deliver it to backends such as Prometheus, Tempo, Jaeger, or Loki.

Around that pipeline sit the conventions that keep the data trustworthy. Semantic conventions agree on attribute names so telemetry means the same thing in every language and tool, while resources, instrumentation scope, and sampling describe where the data came from and how much of it you choose to keep. Taken together, OpenTelemetry is the producer side of observability, and the storage and visualization backends are the consumers.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Signals

Signals are the categories of telemetry OpenTelemetry emits, sharing one API, data model, and context. OTel supports four today and is developing two more:

- **Traces** — the path of a request through your application, as a tree of spans. See [signal-traces.md](signal-traces.md).
- **Metrics** — measurements captured at runtime (counters, gauges, histograms). See [signal-metrics.md](signal-metrics.md).
- **Logs** — timestamped recordings of events, correlated with traces via context. See [signal-logs.md](signal-logs.md).
- **Baggage** — contextual key/value pairs propagated alongside context so one hop can attach data (e.g. a tenant ID) that later hops and signals can read. See [signal-baggage.md](signal-baggage.md).
- **Events** *(in development)* — a specialized kind of log for discrete, well-defined occurrences. See [signal-events.md](signal-events.md).
- **Profiles** *(in development)* — recordings of resource usage at the code level (CPU, memory) for continuous profiling. See [signal-profiles.md](signal-profiles.md).

For how the signals correlate as one model, see [signals.md](signals.md).

### 2. Instrumentation and SDKs

Automatic and manual instrumentation via language SDKs. See [component-instrumentation-and-sdks.md](component-instrumentation-and-sdks.md).

### 3. Context propagation

Carrying trace context across services (W3C Trace Context). See [component-context-propagation.md](component-context-propagation.md).

### 4. The Collector

Receiver → processor → exporter pipeline as a standalone service. See [component-collector.md](component-collector.md).

### 5. Exporters and OTLP

OTLP as the native protocol and exporters to backends. See [component-exporters-and-otlp.md](component-exporters-and-otlp.md).

### 6. Semantic conventions

Standard attribute names for portable, queryable telemetry. See [concept-semantic-conventions.md](concept-semantic-conventions.md).

### 7. Resources, scope, and sampling

Three concepts that shape what telemetry carries and how much of it you keep. A **resource** is the immutable set of attributes describing the entity producing the telemetry — the service name, version, host, and container or pod it runs in — attached to every signal so backends know its origin. The **instrumentation scope** records which library or module emitted a given span, metric, or log, so you can tell first-party code from a dependency. **Sampling** decides which traces to record and export, trading completeness for cost; head sampling chooses up front, tail sampling chooses after a trace completes (e.g. keep only the errors and the slow ones).

### 8. Practical rule

```text
Instrument once with OTel; export OTLP to a Collector; send anywhere.
Follow semantic conventions and propagate context everywhere.
```

---

## Components

The pieces above are concepts; OpenTelemetry ships them as a set of named components, each with its own card in this folder. The list maps the [official components page](https://opentelemetry.io/docs/concepts/components/) onto the deep-dive cards:

- **Specification** — the cross-language contract (API, SDK, data model, OTLP). See [component-specification.md](component-specification.md).
- **Collector** — vendor-agnostic receive/process/export proxy. See [component-collector.md](component-collector.md).
- **Language API & SDK** — per-language implementations you instrument against. See [component-instrumentation-and-sdks.md](component-instrumentation-and-sdks.md).
- **Instrumentation libraries** — prebuilt telemetry for popular frameworks. See [component-instrumentation-libraries.md](component-instrumentation-libraries.md).
- **Zero-code instrumentation** — instrument an app without changing its source. See [component-zero-code-instrumentation.md](component-zero-code-instrumentation.md).
- **Exporters** — emit data to backends; OTLP exporters lose nothing. See [component-exporters-and-otlp.md](component-exporters-and-otlp.md).
- **Resource detectors** — fill the resource from the runtime environment. See [component-resource-detectors.md](component-resource-detectors.md).
- **Cross-service propagators** — carry context across service boundaries. See [component-context-propagation.md](component-context-propagation.md).
- **Samplers** — head sampling to limit how many traces are generated. See [component-samplers.md](component-samplers.md).
- **Kubernetes operator** — manage the Collector and inject instrumentation. See [component-kubernetes-operator.md](component-kubernetes-operator.md).
- **Function-as-a-Service assets** — Lambda layers for serverless functions. See [component-faas-assets.md](component-faas-assets.md).

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
