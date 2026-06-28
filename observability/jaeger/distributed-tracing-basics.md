# Jaeger — distributed tracing basics

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Traces and spans](#1-traces-and-spans)
  * [2. The trace ID](#2-the-trace-id)
  * [3. Context propagation](#3-context-propagation)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

As with any tracing system, a Jaeger trace represents one request's journey through a distributed system, built from spans that each capture a single operation with its timing, tags, and parent. The spans linked by a shared trace ID form a tree that exposes the critical path and where latency accumulates.

Context propagation carries the trace and span IDs across service calls so spans created in different services join the same trace. These ideas are universal to tracing; Jaeger is one backend that stores and visualizes them.

---

## Detailed explanation with examples

### 1. Traces and spans

- TODO: span = one operation; trace = span tree

### 2. The trace ID

- TODO: shared ID joining spans

### 3. Context propagation

- TODO: trace context across service boundaries

### 4. Practical rule

```text
A trace is a tree of spans sharing a trace ID; propagate context everywhere.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use a standard propagation format; add meaningful span tags

### Operations and production

- TODO: verify propagation through gateways/queues to avoid broken traces

## References

- Official docs: https://www.jaegertracing.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../opentelemetry/fundamentals.md](../opentelemetry/fundamentals.md)
