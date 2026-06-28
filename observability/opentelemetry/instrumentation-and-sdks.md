# OpenTelemetry — instrumentation and SDKs

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Automatic instrumentation](#1-automatic-instrumentation)
  * [2. Manual instrumentation](#2-manual-instrumentation)
  * [3. Combining both](#3-combining-both)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Instrumentation is how your application produces telemetry, and OpenTelemetry offers it in two forms. Automatic instrumentation uses language agents or libraries that hook common frameworks — HTTP servers, clients, database drivers — to emit spans and metrics with no code changes, which is the fastest way to get coverage.

Manual instrumentation uses the SDK's API to create custom spans, record metrics, and add attributes for the business logic that auto-instrumentation cannot see. Most systems combine both: auto-instrumentation for breadth, manual for the spans that matter to your domain.

---

## Detailed explanation with examples

### 1. Automatic instrumentation

- TODO: agents/libraries hook frameworks; zero-code coverage

### 2. Manual instrumentation

- TODO: SDK API for custom spans/metrics/attributes

### 3. Combining both

- TODO: auto for breadth, manual for domain-critical spans

### 4. Practical rule

```text
Start with auto-instrumentation; add manual spans for domain-critical paths.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: enable auto-instrumentation; add attributes via semantic conventions

### Operations and production

- TODO: keep SDK/agent versions current; bound custom span/attribute cardinality

## References

- Official docs: https://opentelemetry.io/docs/concepts/instrumentation/
- Overview: [fundamentals.md](fundamentals.md)
