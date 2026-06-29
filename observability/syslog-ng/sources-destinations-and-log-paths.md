# syslog-ng — sources, destinations, and log paths

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Sources and destinations](#1-sources-and-destinations)
  * [2. Log paths](#2-log-paths)
  * [3. Branching paths](#3-branching-paths)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

syslog-ng configuration is built from named objects connected by log paths. A `source` defines where messages come from — the local system, files, or network listeners; a `destination` defines where they go — files, remote servers, databases, or queues; and a `log` path ties one or more sources, optional filters and parsers, and one or more destinations into a single flow.

A message can pass through several log paths, and paths can branch, so the same input can be filtered differently for different outputs. This object-and-path model is the whole configuration structure.

---

## Detailed explanation with examples

### 1. Sources and destinations

- TODO: `source { ... }`, `destination { ... }` objects

### 2. Log paths

- TODO: `log { source(...); filter(...); destination(...); }`

### 3. Branching paths

- TODO: multiple paths; `flags(final)`; same input to many outputs

### 4. Practical rule

```text
Define reusable source/destination objects; connect them in log paths.
Branch paths to send one input to many destinations.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: name and reuse objects; keep log paths readable

### Operations and production

- TODO: ensure a catch-all path so no messages are silently unrouted

## References

- Official docs: https://www.syslog-ng.com/technical-documents/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [filters-and-parsers.md](filters-and-parsers.md)
