# Fluent Bit — Fluent Bit versus Fluentd

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Weight and language](#1-weight-and-language)
  * [2. Roles: edge versus aggregator](#2-roles-edge-versus-aggregator)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Fluent Bit and Fluentd are sibling projects from the same ecosystem, and choosing between them is mostly about weight and role. Fluent Bit is written in C, tiny, and fast, which suits it to running on every node or container as a collector, while Fluentd is written in Ruby, heavier, and has a far larger plugin ecosystem, which suits it to a central aggregator role.

A common architecture uses Fluent Bit at the edge to collect and forward, and Fluentd centrally to aggregate and route to many destinations. Knowing their relative strengths is how you decide which to run where.

---

## Detailed explanation with examples

### 1. Weight and language

- TODO: C, low footprint vs Ruby, larger plugin set

### 2. Roles: edge versus aggregator

- TODO: Fluent Bit as node agent; Fluentd as central aggregator

### 3. Practical rule

```text
Fluent Bit at the edge (collect/forward); Fluentd centrally (aggregate/route).
Often you run both, not one or the other.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: forward edge → aggregator with the `forward` protocol

### Operations and production

- TODO: pick by footprint vs plugin needs; many stacks use Fluent Bit alone now

## References

- Official docs: https://docs.fluentbit.io/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../fluentd/fundamentals.md](../fluentd/fundamentals.md)
