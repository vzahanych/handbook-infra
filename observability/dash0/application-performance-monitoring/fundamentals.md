# Dash0 APM — fundamentals

## Core idea

Application performance monitoring (APM) watches application behavior to find performance bottlenecks — slow endpoints, error rates, throughput, and resource pressure — across the services you instrument. It is the synthesis layer over the raw signals: traces, metrics, and logs combined into service-level health and the golden signals engineers reason about. Built entirely on OpenTelemetry instrumentation, it delivers classic APM insight without a proprietary agent, so the same data also powers the service map, alerting, and Agent0.

---

## Cards in this folder

- [golden-signals.md](golden-signals.md) — latency, traffic, errors, saturation per service.
- [bottleneck-analysis.md](bottleneck-analysis.md) — finding where time and failures concentrate.
- [service-health.md](service-health.md) — rolling signals up into a health view.

---

## References

- Official site: https://www.dash0.com
- Related: [../distributed-tracing/fundamentals.md](../distributed-tracing/fundamentals.md), [../service-map/fundamentals.md](../service-map/fundamentals.md)
