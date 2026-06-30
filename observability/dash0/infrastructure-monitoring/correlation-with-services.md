# Dash0 infrastructure monitoring — correlation with services

## Core idea

The payoff of sharing one store is correlation: an infrastructure signal can be linked to the service symptom it causes. When a node saturates CPU or runs out of memory, the affected service's latency and error traces sit in the same backend, joined by resource attributes, so you can move from "the host is unhealthy" to "this is the request path it is degrading." This collapses the usual gap between infrastructure dashboards and application dashboards into a single investigation.

---

## References

- Official site: https://www.dash0.com
- Related: [../distributed-tracing/fundamentals.md](../distributed-tracing/fundamentals.md), [../service-map/fundamentals.md](../service-map/fundamentals.md)
