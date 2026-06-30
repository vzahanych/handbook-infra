# Dash0 log management — context and correlation

## Core idea

The distinguishing feature is instant context: from a single log line you can pivot to the trace it belongs to, the service that emitted it, and the surrounding lines from the same request. Shared OpenTelemetry attributes and trace ids are the join keys that make this one click instead of a manual search across tools. Correlation is what turns a log from an isolated clue into the entry point of a full investigation.

---

## References

- Official site: https://www.dash0.com
- Related: [../distributed-tracing/errors-and-root-cause.md](../distributed-tracing/errors-and-root-cause.md)
