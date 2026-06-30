# Dash0 APM — golden signals

## Core idea

APM frames service health around the golden signals — latency, traffic, errors, and saturation — derived from the OpenTelemetry spans and metrics each service emits. These four cover most of what matters about a service's behavior with a small, comparable set of numbers, so every service is read the same way. Standardizing on them is what lets dashboards and alerts be templated across an entire fleet instead of bespoke per service.

---

## References

- Official site: https://www.dash0.com
- Related: [../alerting/prebuilt-templates.md](../alerting/prebuilt-templates.md)
