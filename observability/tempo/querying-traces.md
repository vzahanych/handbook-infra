# Tempo — querying traces

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Lookup by trace ID](#1-lookup-by-trace-id)
  * [2. TraceQL search](#2-traceql-search)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

There are two ways to get a trace out of Tempo. The original and cheapest is lookup by trace ID, which you usually obtain by correlation — clicking through from a Loki log line or a Prometheus exemplar in Grafana that carries the ID.

The newer way is TraceQL, a query language that searches traces by span attributes, duration, and structure, letting you find traces matching conditions like requests to checkout slower than two seconds. Knowing both — ID lookup for the common correlated case, TraceQL for exploratory search — covers how you retrieve traces.

---

## Detailed explanation with examples

### 1. Lookup by trace ID

- TODO: direct ID lookup; arrive via correlation

### 2. TraceQL search

- TODO: filter by attributes/duration/structure

### 3. Practical rule

```text
Trace-ID lookup for the correlated case; TraceQL for exploratory search.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: add attributes worth filtering on in TraceQL

### Operations and production

- TODO: ensure indexing supports your TraceQL queries; watch query cost

## References

- Official docs: https://grafana.com/docs/tempo/latest/traceql/
- Overview: [fundamentals.md](fundamentals.md)
