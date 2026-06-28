# Grafana — queries and transformations

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Panel queries](#1-panel-queries)
  * [2. Transformations](#2-transformations)
  * [3. Query versus transformation](#3-query-versus-transformation)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Each panel is driven by queries written in its data source's language, and Grafana adds a transformation layer that reshapes the returned data in the browser before it is drawn. Transformations can join results from multiple queries, compute fields, filter, group, and rename, which lets you build tables and derived views without changing the backend query.

This separation means you express what to fetch in the query and how to shape it in transformations. Knowing where a problem belongs — query versus transformation — keeps panels clear.

---

## Detailed explanation with examples

### 1. Panel queries

- TODO: one or more queries per panel; per-source language

### 2. Transformations

- TODO: join, organize fields, group by, add field from calculation

### 3. Query versus transformation

- TODO: fetch in the query; reshape in transformations

### 4. Practical rule

```text
Fetch the minimum in the query; reshape with transformations.
Don't push work to transformations that the backend can do cheaper.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: minimize data fetched; use transformations for joins/derived fields

### Operations and production

- TODO: watch heavy queries/transform chains that slow dashboards

## References

- Official docs: https://grafana.com/docs/grafana/latest/panels-visualizations/query-transform-data/
- Overview: [fundamentals.md](fundamentals.md)
