# Vector — sources, transforms, sinks

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Sources](#1-sources)
  * [2. Transforms](#2-transforms)
  * [3. Sinks and wiring](#3-sinks-and-wiring)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

A Vector configuration is a graph of three component kinds. Sources collect data — files, syslog, the Kubernetes logs API, OTLP, scraping — and emit events into the pipeline; transforms take events and filter, parse, aggregate, route, or rewrite them; and sinks deliver events to destinations like Elasticsearch, Loki, S3, Kafka, or another Vector.

Components are connected by listing, for each transform or sink, which components feed it, so the topology is an explicit graph rather than a linear order. This graph model is what makes complex routing and fan-out clear.

---

## Detailed explanation with examples

### 1. Sources

- TODO: file, kubernetes_logs, syslog, otlp, http, scrape

### 2. Transforms

- TODO: remap, filter, route, aggregate, reduce

### 3. Sinks and wiring

- TODO: sinks; `inputs = [...]` to wire the graph

### 4. Practical rule

```text
Wire components by naming inputs; the config is a graph, not a sequence.
Use `route`/`filter` transforms to split streams explicitly.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep the graph readable; name components clearly

### Operations and production

- TODO: validate config (`vector validate`); watch per-component metrics

## References

- Official docs: https://vector.dev/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [vrl-the-vector-remap-language.md](vrl-the-vector-remap-language.md)
