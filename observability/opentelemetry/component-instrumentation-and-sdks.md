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

Instrumentation is the work of making an application produce telemetry, and OpenTelemetry offers it in two complementary forms. One is automatic and requires no code changes; the other is manual and lives in your own source. Almost every real system uses a blend of the two.

Automatic instrumentation is the fast path to coverage. A language agent or a set of libraries hooks into the frameworks your application already uses, such as web servers, HTTP clients, and database drivers, and emits spans and metrics for the work those frameworks do. Because it watches the boundaries where requests enter and leave, it gives you broad visibility for very little effort.

Manual instrumentation is where you describe your own logic. Using the application programming interface that the kit provides, you create custom spans, record your own metrics, and attach attributes that capture business meaning the automatic layer cannot see, such as which customer tier a request belongs to. This is the telemetry that turns a generic trace into a story about your domain.

Underneath both sits the software development kit, the configurable engine that actually runs. It is worth separating two ideas here: the interface is the thin surface your code calls, while the kit is the implementation that batches data, applies sampling, and hands telemetry to exporters. You write against the interface and configure the kit, which keeps your instrumentation stable even as the plumbing changes.

The practical guidance follows from this split. Turn on automatic instrumentation first to get breadth across all your boundaries, then add manual spans for the handful of operations that matter most to your domain. Used together, the two forms give you wide coverage without losing the detail that only you can describe.

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
