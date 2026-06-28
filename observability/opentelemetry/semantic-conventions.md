# OpenTelemetry — semantic conventions

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Agreed attribute names](#1-agreed-attribute-names)
  * [2. Why they matter](#2-why-they-matter)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Semantic conventions are OpenTelemetry's agreed names for common attributes, and they are what make telemetry consistent across languages, libraries, and tools. They specify, for example, that an HTTP request's method goes in `http.request.method` and a database system in `db.system`, so a dashboard or query works regardless of which service or language produced the data.

Following the conventions, rather than inventing ad-hoc attribute names, is what lets auto-instrumentation, backends, and queries interoperate. Adhering to semantic conventions is a small discipline that pays off in portable, queryable telemetry.

---

## Detailed explanation with examples

### 1. Agreed attribute names

- TODO: `http.*`, `db.*`, `service.name`, resource attributes

### 2. Why they matter

- TODO: cross-language/tool consistency; dashboards that just work

### 3. Practical rule

```text
Use semantic-convention attribute names; don't invent ad-hoc keys.
Set `service.name` and standard resource attributes everywhere.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: follow current semantic conventions; set resource attributes consistently

### Operations and production

- TODO: enforce naming in the Collector (attribute processors) where needed

## References

- Official docs: https://opentelemetry.io/docs/concepts/semantic-conventions/
- Overview: [fundamentals.md](fundamentals.md)
