# OpenTelemetry — samplers

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Head sampling](#1-head-sampling)
  * [2. Tail sampling](#2-tail-sampling)
  * [3. Parent-based and ratio samplers](#3-parent-based-and-ratio-samplers)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Samplers decide which traces a system actually records and keeps. Their reason to exist is cost: capturing and storing every request at full detail is expensive and usually unnecessary, so a sampler keeps a representative portion and lets the rest go. They let you trade some completeness for a large saving in volume.

As a component, a sampler implements what is called head sampling. This is the decision made right at the start of a trace, inside the kit, before the spans have even been produced. Deciding early is cheap because nothing is recorded for the traces you drop, but it is also blind, since at that moment you cannot yet know whether the request will be slow or fail.

The decision has to be consistent across every service the request touches, or a trace ends up recorded in some services and missing in others. This is why the sampling choice travels inside the propagated context: a parent service makes the call, and its children honor it rather than each flipping their own coin. That shared decision is what keeps a sampled trace whole from end to end.

To make up for the blindness of head sampling, it is often paired with tail sampling in the collector. There the full trace is buffered until it completes, so the decision can be based on what actually happened. A common policy is to keep every trace that contains an error or that ran unusually slowly, while dropping the routine successes that all look the same.

Put together, the two layers give you both economy and signal. Head sampling in the kit cuts the raw volume cheaply and consistently, while tail sampling in the collector rescues the traces that are worth keeping regardless of the dice. The guiding rule is simple: thin out the ordinary traffic, but never throw away your errors and your slow requests.

---

## Detailed explanation with examples

### 1. Head sampling

- TODO: SDK-side, up-front decision; cheap, no full-trace context

### 2. Tail sampling

- TODO: Collector-side, after the trace completes; keep errors/latency outliers

### 3. Parent-based and ratio samplers

- TODO: ParentBased, TraceIdRatioBased, AlwaysOn/Off; consistent decisions across hops

### 4. Practical rule

```text
Head-sample in the SDK for volume; tail-sample in the Collector for signal.
Keep the decision consistent across services via propagated context.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use parent-based ratio sampling in SDKs; propagate the sampling decision

### Operations and production

- TODO: do tail sampling at a gateway Collector; always keep errors and slow traces

## References

- Official docs: https://opentelemetry.io/docs/concepts/sampling/
- Components overview: https://opentelemetry.io/docs/concepts/components/
- Related: [component-collector.md](component-collector.md), [component-context-propagation.md](component-context-propagation.md)
- Overview: [fundamentals.md](fundamentals.md)
