# OpenTelemetry — profiles

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. What a profile records](#1-what-a-profile-records)
  * [2. Continuous profiling](#2-continuous-profiling)
  * [3. Correlation with other signals](#3-correlation-with-other-signals)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

A profile is a recording of resource usage at the level of your code. Where a trace tells you which step of a request was slow, a profile goes one level deeper and tells you which functions inside that step actually consumed the time or the memory. It is the newest of OpenTelemetry's signals and is still under development.

What a profile records is where a program spends its resources. By sampling the call stacks of a running process many times a second, it builds a picture of which functions were on the stack most often, which points to where the central processing unit time is going. The same approach can attribute memory allocations to the code paths that requested them.

The phrase usually attached to this is continuous profiling. Traditionally profiling was something you did by hand on a developer's machine when chasing a specific problem, but continuous profiling means collecting these samples all the time, in production, at a low enough overhead to leave running. That turns profiling from an occasional investigation into an always-available view of where resources go.

The reason OpenTelemetry is adopting profiles as a signal is correlation. By sharing the same resource attributes and context as traces, metrics, and logs, a profile can be tied back to the service, and ideally the request, it came from. The goal is to let you move from a slow trace to the exact lines of code responsible, closing the gap between "this request was slow" and "this function is why."

Because the signal is the least mature, the right posture is to watch it rather than depend on it. The data model and protocol are being defined and the ecosystem support is still arriving, so treat profiles today as a promising direction to understand, not yet a stable production foundation.

---

## Detailed explanation with examples

### 1. What a profile records

- TODO: sampled call stacks; CPU time, memory allocations, other resources; flame-graph view

### 2. Continuous profiling

- TODO: always-on, low-overhead sampling in production vs ad-hoc local profiling

### 3. Correlation with other signals

- TODO: shared resource/context; linking a profile to its service and trace

### 4. Practical rule

```text
Use profiles to find which code consumed CPU or memory, not just which step.
Treat the signal as emerging — track the spec before depending on it.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: align profile resource attributes with other signals for correlation

### Operations and production

- TODO: watch overhead of continuous profiling; track spec/ecosystem maturity before adopting

## References

- Official docs: https://opentelemetry.io/docs/concepts/signals/
- Related: [signal-traces.md](signal-traces.md), [signals.md](signals.md)
- Overview: [fundamentals.md](fundamentals.md)
