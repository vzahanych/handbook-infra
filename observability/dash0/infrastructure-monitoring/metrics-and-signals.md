# Dash0 infrastructure monitoring — metrics and signals

## Core idea

Infrastructure health is read from the classic resource signals — CPU, memory, disk, network, and process-level metrics — collected via OpenTelemetry host and system receivers. These are the saturation and utilization indicators that reveal whether the platform has headroom or is being starved. Collected as standard OTel metrics, they query with PromQL and drive the same alerting and dashboard machinery as everything else in Dash0.

---

## References

- Official site: https://www.dash0.com
- Related: [../alerting/promql-checks.md](../alerting/promql-checks.md)
