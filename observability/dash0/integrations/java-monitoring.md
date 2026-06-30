# Dash0 integrations — Java monitoring

## Core idea

Java monitoring brings comprehensive observability to JVM-based services through OpenTelemetry's Java instrumentation, typically the auto-instrumentation agent that wires up common frameworks without code changes. It highlights JVM-specific concerns — heap and GC behavior, thread pools, and spans from servlet, JDBC, and messaging libraries — alongside the standard signals. As with every Dash0 integration, the output is plain OTLP, so it lands in the shared store and feeds the service map and alerting.

---

## References

- Official site: https://www.dash0.com
- Related: [../../opentelemetry/component-instrumentation-and-sdks.md](../../opentelemetry/component-instrumentation-and-sdks.md)
