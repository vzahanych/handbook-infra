# Grafana — variables and templating

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Template variables](#1-template-variables)
  * [2. Query and chained variables](#2-query-and-chained-variables)
  * [3. Using variables in panels](#3-using-variables-in-panels)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Template variables are what make a Grafana dashboard reusable instead of hard-coded. A variable holds a value — often populated from a query, like the list of hosts or namespaces — and is referenced in panel queries with a `$name` placeholder, so changing the variable repoints every panel at once.

This turns a single dashboard into one that works across environments, clusters, or services through a dropdown. Designing variables well, including chained variables that filter each other, is the difference between one dashboard and dozens of copies.

---

## Detailed explanation with examples

### 1. Template variables

- TODO: variable types; `$var` substitution

### 2. Query and chained variables

- TODO: query-populated variables; one variable filtering another

### 3. Using variables in panels

- TODO: variables in queries, titles, links; multi-value/`All`

### 4. Practical rule

```text
Parameterize dashboards with variables instead of duplicating them.
Use chained query variables to filter (cluster → namespace → pod).
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: build one reusable dashboard with variables, not many copies

### Operations and production

- TODO: bound multi-value/`All` expansions to avoid huge queries

## References

- Official docs: https://grafana.com/docs/grafana/latest/dashboards/variables/
- Overview: [fundamentals.md](fundamentals.md)
