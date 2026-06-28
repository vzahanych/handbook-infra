# Loki — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The log data model](#1-the-log-data-model)
  * [2. Labels and streams](#2-labels-and-streams)
  * [3. LogQL](#3-logql)
  * [4. Ingestion and agents](#4-ingestion-and-agents)
  * [5. Storage and retention](#5-storage-and-retention)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Loki is a log aggregation system designed to be cost-efficient by indexing only metadata, not the log text. Where a full-text engine indexes every word, Loki indexes just a small set of labels per log stream and stores the raw log lines compressed in object storage, which makes it cheap to run at scale. It is often described as "Prometheus for logs" because it borrows the same label-based model and pairs naturally with Grafana.

Querying uses LogQL, a language modeled on PromQL that first selects log streams by label and then filters and parses the lines within them. The consequence of indexing only labels is that label design drives everything: well-chosen, low-cardinality labels make queries fast and storage cheap, while high-cardinality labels break the model.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. The log data model

Timestamped lines grouped into label-defined streams; content is not indexed. See [the-log-data-model.md](the-log-data-model.md).

### 2. Labels and streams

Labels are the only index; cardinality discipline is everything. See [labels-and-streams.md](labels-and-streams.md).

### 3. LogQL

Stream selectors then line filters/parsers, plus metrics from logs. See [logql.md](logql.md).

### 4. Ingestion and agents

Promtail/Alloy/OTel collecting, labelling, and shipping logs. See [ingestion-and-agents.md](ingestion-and-agents.md).

### 5. Storage and retention

Small index plus cheap object-stored chunks, and retention. See [storage-and-retention.md](storage-and-retention.md).

### 6. Practical rule

```text
Index labels, not content; keep labels low-cardinality.
Query with a tight `{label=...}` selector first, then filter lines.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use few, bounded labels (app/namespace/env); never label by request/user/trace id
- TODO: put high-variety data in the line; extract at query time

### Operations and production

- TODO: back chunks with object storage; set retention per tenant/stream
- TODO: monitor stream/chunk counts and per-tenant limits

## References

- Official docs: https://grafana.com/docs/loki/latest/
- Related: [../grafana/fundamentals.md](../grafana/fundamentals.md), [../prometheus/fundamentals.md](../prometheus/fundamentals.md)
