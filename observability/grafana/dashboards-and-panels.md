# Grafana — dashboards and panels

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Panels and visualizations](#1-panels-and-visualizations)
  * [2. Dashboards as JSON](#2-dashboards-as-json)
  * [3. Rows and folders](#3-rows-and-folders)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

A Grafana dashboard is a collection of panels arranged on a grid, where each panel runs one or more queries against a data source and visualizes the result. Panels come in types — time series, stat, gauge, table, bar, heatmap — and choosing the right visualization for the data is most of building a useful dashboard.

Dashboards are stored as JSON, which is what lets them be exported, versioned, and shared. Organizing related panels into rows and folders keeps large dashboards navigable.

---

## Detailed explanation with examples

### 1. Panels and visualizations

- TODO: time series, stat, gauge, table, heatmap; pick by data

### 2. Dashboards as JSON

- TODO: JSON model; export/import; versioning

### 3. Rows and folders

- TODO: rows for grouping; folders + permissions

### 4. Practical rule

```text
Choose the visualization that fits the data; group panels in rows/folders.
Treat the dashboard JSON as the source of truth.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep panels focused; avoid over-dense dashboards

### Operations and production

- TODO: store dashboard JSON in version control; organize with folders

## References

- Official docs: https://grafana.com/docs/grafana/latest/dashboards/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [queries-and-transformations.md](queries-and-transformations.md)
