# Vector — topology and deployment roles

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Agent role](#1-agent-role)
  * [2. Aggregator role](#2-aggregator-role)
  * [3. Tiered topology](#3-tiered-topology)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Vector is typically deployed in one or both of two roles, mirroring the edge-versus-aggregator pattern. In the agent role it runs on each host or node, collecting local logs and metrics and forwarding them; in the aggregator role it runs as a central service that receives from many agents, does heavier transformation and routing, and ships to backends.

Because it is a single efficient binary that does both, you can build a tiered topology — agents forwarding to aggregators — entirely with Vector. Choosing the role per instance is the main deployment decision.

---

## Detailed explanation with examples

### 1. Agent role

- TODO: per-node collection and forwarding

### 2. Aggregator role

- TODO: central receive, transform, route to backends

### 3. Tiered topology

- TODO: agents → aggregators via the `vector` source/sink

### 4. Practical rule

```text
Agents collect/forward; aggregators transform/route.
Do heavy VRL and fan-out at the aggregator tier.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep agent configs light; centralize transformation at aggregators

### Operations and production

- TODO: scale aggregators horizontally; secure agent→aggregator transport (TLS)

## References

- Official docs: https://vector.dev/docs/setup/deployment/
- Overview: [fundamentals.md](fundamentals.md)
