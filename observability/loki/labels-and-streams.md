# Loki — labels and streams

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Labels define streams](#1-labels-define-streams)
  * [2. Cardinality](#2-cardinality)
  * [3. Where high-variety data goes](#3-where-high-variety-data-goes)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Labels in Loki identify streams and are the only thing indexed, which makes their design the central decision. Good labels describe the source — things like `app`, `namespace`, `env` — and have a small, bounded set of values.

The danger is the same cardinality trap as in Prometheus: putting high-variety values like request IDs, user IDs, or trace IDs into labels creates an explosion of tiny streams that wrecks performance and cost. Such high-variety data belongs in the log line, to be extracted at query time, not in a label.

---

## Detailed explanation with examples

### 1. Labels define streams

- TODO: each unique label set is a stream

### 2. Cardinality

- TODO: high-variety labels → stream explosion

### 3. Where high-variety data goes

- TODO: keep ids in the line; extract with LogQL parsers

### 4. Practical rule

```text
Few bounded labels (app/namespace/env). Never label by id/request/trace.
Put high-variety data in the line and parse it at query time.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: standardize a small label set; reject dynamic labels at ingestion

### Operations and production

- TODO: alert on stream/cardinality growth; enforce per-tenant limits

## References

- Official docs: https://grafana.com/docs/loki/latest/get-started/labels/
- Overview: [fundamentals.md](fundamentals.md)
