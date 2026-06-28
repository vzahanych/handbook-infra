# Tempo — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Distributed tracing basics](#1-distributed-tracing-basics)
  * [2. Trace ingestion](#2-trace-ingestion)
  * [3. Storage and object backends](#3-storage-and-object-backends)
  * [4. Querying traces](#4-querying-traces)
  * [5. Metrics and correlation](#5-metrics-and-correlation)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Tempo is a distributed tracing backend designed, like Loki, around cheap object storage and minimal indexing. It ingests traces — records of how a single request flows through many services — in all the common formats (OpenTelemetry, Jaeger, Zipkin) and stores them as compressed blocks in object storage, without the large index a traditional tracing store needs. This makes retaining huge volumes of traces affordable.

Because it indexes little, Tempo's original sweet spot is looking up a trace by its ID, usually obtained from a correlated log or metric. Newer versions add TraceQL for searching traces by attributes, but the design still leans on correlation: jump from a Grafana metric or log to the exact trace. Tempo is built to be the trace store in a Prometheus-Loki-Tempo stack.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Distributed tracing basics

Traces, spans, the trace ID, and context propagation. See [distributed-tracing-basics.md](distributed-tracing-basics.md).

### 2. Trace ingestion

Receiving OTLP/Jaeger/Zipkin via a collector, and upstream sampling. See [trace-ingestion.md](trace-ingestion.md).

### 3. Storage and object backends

Compressed blocks in object storage and minimal indexing. See [storage-and-object-backends.md](storage-and-object-backends.md).

### 4. Querying traces

Trace-ID lookup and TraceQL search. See [querying-traces.md](querying-traces.md).

### 5. Metrics and correlation

Exemplars, log-to-trace links, and span-derived metrics. See [metrics-and-correlation.md](metrics-and-correlation.md).

### 6. Practical rule

```text
Store traces cheaply in object storage; reach them mostly by correlated trace ID.
Use TraceQL for exploratory search; sample upstream, not in Tempo.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: emit OTLP; propagate context; sample at SDK/collector
- TODO: link metrics/logs to traces via exemplars and trace IDs

### Operations and production

- TODO: back blocks with object storage; run the compactor; set retention
- TODO: monitor ingestion rate and dropped spans

## References

- Official docs: https://grafana.com/docs/tempo/latest/
- Related: [../grafana/fundamentals.md](../grafana/fundamentals.md), [../opentelemetry/fundamentals.md](../opentelemetry/fundamentals.md)
