# Dash0 Agent0 — fundamentals

## Core idea

Agent0 is Dash0's autonomous AI engineer for production: it continuously watches all services and signals, detects issues before they reach customers, and investigates them down to root cause by correlating traces, logs, and metrics. Crucially it acts rather than just advises — it reads your codebase, ties a root cause in a trace to the responsible source code, and produces production-ready assets such as pull requests, dashboards, alert rules, and instrumentation guides. It connects to where teams already work via GitHub, Linear, and any Model Context Protocol (MCP) server, and it is billed on task-based credits where a task is a meaningful unit of work.

---

## Cards in this folder

- [issue-detection-and-investigation.md](issue-detection-and-investigation.md) — continuous detection and root-cause investigation.
- [root-cause-and-code.md](root-cause-and-code.md) — linking a trace to the responsible source code.
- [automated-assets-and-prs.md](automated-assets-and-prs.md) — PRs, dashboards, alerts, and guides it generates.
- [stack-integration-mcp.md](stack-integration-mcp.md) — GitHub, Linear, and MCP connections.
- [task-based-pricing.md](task-based-pricing.md) — the credit model that meters it.

---

## References

- Official site: https://www.dash0.com
- Related: [../service-map/fundamentals.md](../service-map/fundamentals.md), [../distributed-tracing/fundamentals.md](../distributed-tracing/fundamentals.md)
