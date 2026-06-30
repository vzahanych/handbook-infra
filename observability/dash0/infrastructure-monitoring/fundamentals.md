# Dash0 infrastructure monitoring — fundamentals

## Core idea

Infrastructure monitoring tracks the health and performance of the underlying compute — hosts, nodes, and infrastructure components — by ingesting their metrics and logs through OpenTelemetry and presenting them with ready-made views. It answers the "is the platform underneath my apps healthy?" question: CPU, memory, disk, network, and process-level signals seen in one place. Because the data shares the OTLP store with traces and application metrics, infrastructure problems can be tied directly to the user-facing symptoms they cause.

---

## Cards in this folder

- [hosts-and-resources.md](hosts-and-resources.md) — the host and resource model being monitored.
- [metrics-and-signals.md](metrics-and-signals.md) — the core resource signals collected.
- [correlation-with-services.md](correlation-with-services.md) — linking infra health to service symptoms.

---

## References

- Official site: https://www.dash0.com
- Related: [../kubernetes-monitoring/fundamentals.md](../kubernetes-monitoring/fundamentals.md), [../../prometheus/fundamentals.md](../../prometheus/fundamentals.md)
