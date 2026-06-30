# Dash0 service map — topology from traces

## Core idea

The map is built automatically from trace data: every span that calls another service is an edge, and the accumulation of spans reveals the real topology. Because it is derived from actual requests rather than a hand-drawn diagram, the graph reflects how the system truly behaves and stays current as calls change. Aggregated error and latency rates on each edge turn the topology into a health view, not just a wiring diagram.

---

## References

- Official site: https://www.dash0.com
- Related: [../distributed-tracing/spans-and-context.md](../distributed-tracing/spans-and-context.md)
