# Jaeger — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Distributed tracing basics](#1-distributed-tracing-basics)
  * [2. Architecture and components](#2-architecture-and-components)
  * [3. Spans and context propagation](#3-spans-and-context-propagation)
  * [4. Sampling](#4-sampling)
  * [5. Storage backends](#5-storage-backends)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Jaeger is a distributed tracing system, originally from Uber, for capturing and visualizing how requests flow through microservices. Applications instrumented to emit spans send them to Jaeger, which assembles them into traces and provides a UI to search, view, and analyze request paths and latencies. It pairs naturally with OpenTelemetry, now the recommended way to instrument applications that report to Jaeger.

Unlike Tempo's index-light, object-storage-first design, Jaeger uses pluggable storage backends — such as Cassandra, Elasticsearch, or OpenSearch — that index spans for rich search by service, operation, tags, and duration. Its model centers on spans, context propagation, sampling to control volume, and a set of components that receive, process, store, and query traces.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Distributed tracing basics

Traces, spans, the trace ID, and propagation. See [distributed-tracing-basics.md](distributed-tracing-basics.md).

### 2. Architecture and components

The receive → process → store → query pipeline (and the OTel Collector). See [architecture-and-components.md](architecture-and-components.md).

### 3. Spans and context propagation

Span tags/logs/parent and propagating trace context across services. See [spans-and-context-propagation.md](spans-and-context-propagation.md).

### 4. Sampling

Head-based and remote sampling to control trace volume. See [sampling.md](sampling.md).

### 5. Storage backends

Cassandra/Elasticsearch/OpenSearch and dev backends. See [storage-backends.md](storage-backends.md).

### 6. Practical rule

```text
Instrument with OpenTelemetry; sample to control volume; tag spans for search.
Pick and size a storage backend — it defines search and ops burden.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: instrument via OpenTelemetry; propagate context; add searchable tags
- TODO: choose a sampling strategy that balances coverage and cost

### Operations and production

- TODO: run a production backend (Cassandra/Elasticsearch); size and scale it
- TODO: monitor dropped spans and storage growth

## References

- Official docs: https://www.jaegertracing.io/docs/
- Related: [../opentelemetry/fundamentals.md](../opentelemetry/fundamentals.md), [../tempo/fundamentals.md](../tempo/fundamentals.md)
