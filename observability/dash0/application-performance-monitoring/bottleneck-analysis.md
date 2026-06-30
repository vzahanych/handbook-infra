# Dash0 APM — bottleneck analysis

## Core idea

Bottleneck analysis pinpoints where latency and failures concentrate by aggregating traces to reveal the consistently slow operations, not just one anomalous request. Looking across many traces separates a systemic hotspot — a slow query, a saturated dependency — from random noise. From an aggregate hotspot you drop into an exemplar trace to see the offending span, connecting the statistical view to a concrete piece of work.

---

## References

- Official site: https://www.dash0.com
- Related: [../distributed-tracing/waterfall-and-latency.md](../distributed-tracing/waterfall-and-latency.md)
