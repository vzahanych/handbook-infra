# Alertmanager — the routing tree

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Root and child routes](#1-root-and-child-routes)
  * [2. Matching by label](#2-matching-by-label)
  * [3. Per-route timing](#3-per-route-timing)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Routing in Alertmanager is a tree: a top-level route catches every alert and child routes match subsets by label, so an alert flows down to the most specific matching node, which determines its receiver and timing. Each route can set the receiver, the grouping keys, and timing parameters like how long to wait before sending and how often to repeat.

Because matching is by label, the routing tree is where you encode policy — team ownership, severity, environment — entirely from alert labels. Designing a clear routing tree is the main configuration task.

---

## Detailed explanation with examples

### 1. Root and child routes

- TODO: catch-all root; nested routes; `continue`

### 2. Matching by label

- TODO: `match`/`matchers`; most-specific wins

### 3. Per-route timing

- TODO: `group_wait`, `group_interval`, `repeat_interval`

### 4. Practical rule

```text
Encode ownership/severity/env in the routing tree via label matchers.
Set a default receiver at the root; specialize in child routes.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep the tree shallow and label-driven; always have a catch-all

### Operations and production

- TODO: validate routing with `amtool`; review routes as code

## References

- Official docs: https://prometheus.io/docs/alerting/latest/configuration/
- Overview: [fundamentals.md](fundamentals.md)
