# Dash0 OpenTelemetry-native — semantic conventions

## Core idea

Dash0 relies on OpenTelemetry semantic conventions — the standard names for resource and span attributes — to make telemetry consistent and queryable across languages and sources. Because every service tags data with the same well-known keys (service.name, http.route, k8s.pod.name, and so on), Dash0 can group, filter, and correlate signals without per-app mapping. Conventions are what turn a pile of attributes into a coherent model the service map, dashboards, and Agent0 can all reason over.

---

## References

- Official site: https://www.dash0.com
- Related: [../../opentelemetry/concept-semantic-conventions.md](../../opentelemetry/concept-semantic-conventions.md)
