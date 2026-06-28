# Tempo — distributed tracing basics

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

A trace records the path of a single request as it moves through a distributed system, and it is made of spans, each representing one unit of work such as an HTTP handler or a database call. Spans carry a start time, duration, attributes, and parent-child links, so together they form a tree that shows where time went and which service called which.

Every span shares a trace ID, and context propagation passes that ID across service boundaries so the pieces can be stitched back together. Understanding spans, the trace ID, and propagation is the foundation for any tracing backend, Tempo included.

---

## Detailed explanation with examples

### 1. Traces and spans

- TODO: span = unit of work; trace = span tree

### 2. The trace ID

- TODO: shared ID stitching spans together

### 3. Context propagation

- TODO: passing trace context across service boundaries

### 4. Practical rule

```text
A trace is a tree of spans sharing one trace ID.
Propagation across services is what makes it whole — instrument it everywhere.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use a standard propagation format (W3C tracecontext); add useful span attributes

### Operations and production

- TODO: ensure propagation through gateways/queues so traces aren't broken

## References

- Official docs: https://grafana.com/docs/tempo/latest/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../opentelemetry/fundamentals.md](../opentelemetry/fundamentals.md)
