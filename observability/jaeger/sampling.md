# Jaeger — sampling

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Head-based sampling](#1-head-based-sampling)
  * [2. Remote sampling](#2-remote-sampling)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Tracing every request at full volume is usually too expensive, so Jaeger relies on sampling to decide which traces to record. Head-based sampling makes the keep-or-drop decision at the start of a trace, using strategies like a fixed probability or a rate limit, and the decision propagates so a whole trace is consistently kept or dropped.

Jaeger also supports remote sampling, where the collector centrally distributes per-service sampling strategies that clients fetch, letting you tune sampling without redeploying. Choosing a sampling strategy is the main lever for balancing trace coverage against cost.

---

## Detailed explanation with examples

### 1. Head-based sampling

- TODO: probabilistic / rate-limiting; decision propagates

### 2. Remote sampling

- TODO: collector-distributed per-service strategies

### 3. Practical rule

```text
Sample to control cost; keep the decision consistent across a trace.
Use remote sampling to tune per-service without redeploys.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: pick probabilistic vs rate-limiting per service; consider tail sampling in the collector

### Operations and production

- TODO: centralize strategies via remote sampling; monitor effective sample rates

## References

- Official docs: https://www.jaegertracing.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
