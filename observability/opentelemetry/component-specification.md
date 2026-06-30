# OpenTelemetry — the Specification

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. API, SDK, and data model](#1-api-sdk-and-data-model)
  * [2. OTLP and semantic conventions](#2-otlp-and-semantic-conventions)
  * [3. Stability and versioning](#3-stability-and-versioning)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

The specification is the written contract that defines what every OpenTelemetry implementation must do. It is the reason a trace produced by the Go library means the same thing as one produced by the Python library: both are built to satisfy the same document. Rather than something you install, it is the single source of truth that all the language implementations are measured against.

Its first concern is the application programming interface, the surface that your code and the instrumentation libraries call to create telemetry. The specification fixes how that interface behaves, so that the act of starting a span or recording a measurement is identical in spirit across every language, even though the syntax differs.

Its second concern is the software development kit, the configurable implementation that sits behind the interface. Here the specification lays out the requirements each language binding must meet, covering how sampling decisions are made, how data is batched, and how it is handed to exporters, so that the kits behave consistently rather than each inventing its own rules.

Its third concern is the shape of the data on the wire. The specification defines the data model for each signal and the OpenTelemetry Protocol that carries them, together with the semantic conventions that name attributes. This is what lets any compliant producer and any compliant backend understand one another without private agreements.

Because the behavior is specified once and implemented many times, the specification is the thing that makes OpenTelemetry portable in the first place. It also evolves carefully, marking each part as experimental or stable so you know what you can depend on. Every other component described in this folder ultimately derives its required behavior from this one document.

---

## Detailed explanation with examples

### 1. API, SDK, and data model

- TODO: API (what app code calls) vs SDK (the configurable implementation) vs data model (the shape on the wire)

### 2. OTLP and semantic conventions

- TODO: OTLP defined by the spec; semantic conventions standardize attribute names across languages

### 3. Stability and versioning

- TODO: per-signal stability levels (stable/experimental); how guarantees evolve

### 4. Practical rule

```text
The spec is the contract; SDKs are implementations of it.
Code against the API and rely on spec-stable behavior, not SDK internals.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: depend on the stable API surface; avoid experimental spec features in production paths

### Operations and production

- TODO: track spec stability levels when upgrading SDKs across languages

## References

- Official docs: https://opentelemetry.io/docs/specs/otel/
- Components overview: https://opentelemetry.io/docs/concepts/components/
- Overview: [fundamentals.md](fundamentals.md)
