# Dash0 APM — service health

## Core idea

Service health rolls the per-operation signals up into a single, per-service status that answers "is this service okay right now?" Aggregating latency, error rate, and throughput at the service level gives operators a stable overview before they drill into individual traces. This rolled-up view is also what the service map renders on each node and what alerting watches for regressions.

---

## References

- Official site: https://www.dash0.com
- Related: [../service-map/fundamentals.md](../service-map/fundamentals.md), [../alerting/fundamentals.md](../alerting/fundamentals.md)
