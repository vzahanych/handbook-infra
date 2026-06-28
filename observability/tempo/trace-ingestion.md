# Tempo — trace ingestion

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Supported protocols](#1-supported-protocols)
  * [2. The collector in front](#2-the-collector-in-front)
  * [3. Sampling upstream](#3-sampling-upstream)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Tempo accepts traces over the protocols applications already emit, including OpenTelemetry (OTLP), Jaeger, and Zipkin, so you point your instrumentation or collector at Tempo without changing how you produce spans. Typically an OpenTelemetry Collector sits in front, receiving spans from services, batching them, and forwarding to Tempo.

Because trace volume can be enormous, sampling — deciding which traces to keep — is usually applied upstream at the SDK or collector rather than in Tempo. The ingestion path is mostly about receiving and batching; the cleverness is in cheap storage behind it.

---

## Detailed explanation with examples

### 1. Supported protocols

- TODO: OTLP, Jaeger, Zipkin receivers

### 2. The collector in front

- TODO: OTel Collector receives/batches/forwards

### 3. Sampling upstream

- TODO: head vs tail sampling at SDK/collector

### 4. Practical rule

```text
Send OTLP via a collector; batch before Tempo.
Sample upstream (SDK/collector), not in Tempo.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: standardize on OTLP; choose head/tail sampling deliberately

### Operations and production

- TODO: size collector batching/queues; monitor refused/dropped spans

## References

- Official docs: https://grafana.com/docs/tempo/latest/
- Overview: [fundamentals.md](fundamentals.md)
