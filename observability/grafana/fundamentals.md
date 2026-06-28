# Grafana — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Data sources](#1-data-sources)
  * [2. Dashboards and panels](#2-dashboards-and-panels)
  * [3. Queries and transformations](#3-queries-and-transformations)
  * [4. Variables and templating](#4-variables-and-templating)
  * [5. Alerting](#5-alerting)
  * [6. Provisioning and dashboards as code](#6-provisioning-and-dashboards-as-code)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Grafana is a visualization and exploration layer that sits on top of other systems rather than storing data itself. You connect it to data sources — Prometheus, Loki, Tempo, SQL databases, and many more — and build dashboards of panels that query those sources and render the results as graphs, tables, and stat tiles. Because it queries live, Grafana shows current data from each backend in that backend's own query language.

The pieces that make Grafana powerful are templating variables that make dashboards reusable across environments and targets, transformations that reshape query results in the browser, and a unified alerting system. Treating dashboards as configuration that can be provisioned from files, rather than hand-built and forgotten, is what keeps Grafana maintainable at scale.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Data sources

Configured connections to backends, each with its own query language. See [data-sources.md](data-sources.md).

### 2. Dashboards and panels

Panels on a grid, panel types, and dashboards as JSON. See [dashboards-and-panels.md](dashboards-and-panels.md).

### 3. Queries and transformations

Per-panel queries and the browser-side transformation layer. See [queries-and-transformations.md](queries-and-transformations.md).

### 4. Variables and templating

Template variables that make dashboards reusable. See [variables-and-templating.md](variables-and-templating.md).

### 5. Alerting

Grafana unified alerting: rules, notification policies, contact points. See [alerting.md](alerting.md).

### 6. Provisioning and dashboards as code

Provisioning from files and dashboards-as-code. See [provisioning-and-dashboards-as-code.md](provisioning-and-dashboards-as-code.md).

### 7. Practical rule

```text
Grafana queries backends live; build reusable dashboards with variables.
Manage dashboards and data sources as code to avoid drift.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use template variables for reuse; shape data with transformations, fetch minimal data in queries
- TODO: pick the panel type that fits the data

### Operations and production

- TODO: provision data sources/dashboards/alerts from files; version dashboards as code
- TODO: control access with folders/permissions; avoid UI-only changes that drift

## References

- Official docs: https://grafana.com/docs/grafana/latest/
- Related: [../prometheus/fundamentals.md](../prometheus/fundamentals.md)
