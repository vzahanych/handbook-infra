# Jaeger — spans and context propagation

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Span anatomy](#1-span-anatomy)
  * [2. Tags for search](#2-tags-for-search)
  * [3. Propagation](#3-propagation)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

A span in Jaeger records one operation with a start time, duration, a set of key-value tags, logs, and a reference to its parent, and spans are the atoms traces are built from. Tags are what make traces searchable — service, operation, HTTP status, error flags — so attaching meaningful tags is part of good instrumentation.

Context propagation passes the trace context, including the trace and span IDs, through headers across service boundaries, and consistent propagation is what keeps a trace from fragmenting. The richer and more consistent the span tags and propagation, the more useful the traces.

---

## Detailed explanation with examples

### 1. Span anatomy

- TODO: start/duration, tags, logs, parent reference

### 2. Tags for search

- TODO: service/operation/status/error tags drive UI search

### 3. Propagation

- TODO: trace context in headers across services

### 4. Practical rule

```text
Tag spans with what you'll search by; propagate context consistently.
Inconsistent propagation fragments traces.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: standardize tag keys (semantic conventions); mark errors on spans

### Operations and production

- TODO: audit for broken propagation across hops

## References

- Official docs: https://www.jaegertracing.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
