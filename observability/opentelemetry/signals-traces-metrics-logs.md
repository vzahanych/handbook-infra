# OpenTelemetry — signals: traces, metrics, logs

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The three signals](#1-the-three-signals)
  * [2. One correlated model](#2-one-correlated-model)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

OpenTelemetry models observability as three signals — traces, metrics, and logs — under one consistent API and data model. Traces capture the path of a request as spans, metrics capture numeric measurements over time, and logs capture timestamped events, and OTel's value is treating them together so they share context and attributes.

Because all three flow through the same SDKs and protocol, a trace ID can tie a slow span to its metrics and logs. Understanding the three signals as one correlated whole is the core OTel idea.

---

## Detailed explanation with examples

### 1. The three signals

- TODO: traces (spans), metrics (measurements), logs (events)

### 2. One correlated model

- TODO: shared context/attributes; trace ID linking signals

### 3. Practical rule

```text
Treat traces, metrics, and logs as one correlated set, not three silos.
Share context so you can pivot between them.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: attach trace context to logs and exemplars to metrics

### Operations and production

- TODO: route each signal to the right backend while keeping correlation

## References

- Official docs: https://opentelemetry.io/docs/concepts/signals/
- Overview: [fundamentals.md](fundamentals.md)
