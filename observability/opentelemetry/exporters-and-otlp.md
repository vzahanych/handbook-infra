# OpenTelemetry — exporters and OTLP

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. OTLP, the native protocol](#1-otlp-the-native-protocol)
  * [2. Exporters](#2-exporters)
  * [3. Portability](#3-portability)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

OTLP, the OpenTelemetry Protocol, is the native wire format for all three signals, and exporters are the components that send telemetry out using it or other formats. An application or Collector configures exporters to deliver data to a destination — OTLP to a Collector or backend, or backend-specific exporters for systems that do not speak OTLP.

Standardizing on OTLP is what makes telemetry portable: you can change backends by reconfiguring exporters rather than re-instrumenting code. Treating OTLP as the lingua franca is the practical benefit of adopting OpenTelemetry.

---

## Detailed explanation with examples

### 1. OTLP, the native protocol

- TODO: OTLP over gRPC/HTTP for traces/metrics/logs

### 2. Exporters

- TODO: OTLP exporter; backend-specific exporters

### 3. Portability

- TODO: change backends by reconfiguring exporters

### 4. Practical rule

```text
Standardize on OTLP; switch backends by reconfiguring exporters, not code.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: export OTLP from apps; do backend translation in the Collector

### Operations and production

- TODO: secure OTLP endpoints (TLS/auth); monitor export failures/retries

## References

- Official docs: https://opentelemetry.io/docs/specs/otlp/
- Overview: [fundamentals.md](fundamentals.md)
