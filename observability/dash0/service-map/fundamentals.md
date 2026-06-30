# Dash0 service map — fundamentals

## Core idea

The service map is Dash0's visual representation of service dependencies and how requests flow between them, derived automatically from trace data. It turns the implicit topology in your spans into an explicit graph, exposing which services call which and where errors or latency concentrate along those edges. As a navigational surface it lets you move from the big-picture architecture down into the traces, logs, and metrics of any node, and it gives Agent0 the dependency context it needs to reason about blast radius.

---

## Cards in this folder

- [topology-from-traces.md](topology-from-traces.md) — how the graph is built from spans.
- [navigation-and-drilldown.md](navigation-and-drilldown.md) — using the map to investigate.

---

## References

- Official site: https://www.dash0.com
- Related: [../distributed-tracing/fundamentals.md](../distributed-tracing/fundamentals.md), [../agent0/fundamentals.md](../agent0/fundamentals.md)
