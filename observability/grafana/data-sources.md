# Grafana — data sources

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Connections, not storage](#1-connections-not-storage)
  * [2. Per-source query languages](#2-per-source-query-languages)
  * [3. Default and mixed sources](#3-default-and-mixed-sources)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Grafana does not hold metrics or logs; it queries data sources, which are configured connections to backends like Prometheus, Loki, Tempo, Elasticsearch, or a SQL database. Each data source type brings its own query editor and query language, so a Prometheus panel uses PromQL while a Loki panel uses LogQL, all within the same dashboard.

A default data source can be set, and panels can mix sources or use a special mixed source. Configuring data sources — and provisioning them from files rather than the UI — is the foundation everything else queries through.

---

## Detailed explanation with examples

### 1. Connections, not storage

- TODO: Grafana stores no telemetry; it queries backends

### 2. Per-source query languages

- TODO: PromQL, LogQL, TraceQL, SQL per data source type

### 3. Default and mixed sources

- TODO: default source; the `-- Mixed --` source

### 4. Practical rule

```text
Pick the data source per panel; each has its own query language.
Provision data sources from files, not the UI.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use a sensible default source; reference sources by UID in JSON

### Operations and production

- TODO: provision data sources as code; store credentials in secrets

## References

- Official docs: https://grafana.com/docs/grafana/latest/datasources/
- Overview: [fundamentals.md](fundamentals.md)
