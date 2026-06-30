# Dash0 infrastructure monitoring — hosts and resources

## Core idea

The unit of infrastructure monitoring is the host or infrastructure resource — a VM, bare-metal node, or managed component — identified by OpenTelemetry resource attributes. Tagging each resource with conventional keys lets Dash0 group signals by host, environment, or provider and present them as coherent entities rather than loose metric streams. This entity model is the anchor everything else hangs from: alerts, dashboards, and service correlation all reference these resources.

---

## References

- Official site: https://www.dash0.com
- Related: [../opentelemetry-native/semantic-conventions.md](../opentelemetry-native/semantic-conventions.md)
