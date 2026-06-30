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

Semantic conventions are OpenTelemetry's agreed vocabulary for describing telemetry. Telemetry is full of attributes, which are the key and value pairs attached to a span, a metric, or a log, and the conventions decide what those keys should be called and what they mean. They are the shared dictionary that lets data from different sources line up.

The conventions cover the operations you see again and again. For a web request, for instance, they specify that the method always lives under the attribute named http dot request dot method, and that the database engine behind a query lives under db dot system. Because the name is fixed, a dashboard built for one service keeps working when the data comes from a completely different service or language.

They also describe the entity producing the data, not just the operation. Resource attributes such as service dot name, service dot version, and the host or container details follow the same agreed naming, so backends can group and filter telemetry by where it originated. The same discipline that standardizes a request also standardizes its source.

The reason this matters is interoperability. When everyone uses the same names, automatic instrumentation, collectors, backends, and the queries you write all understand each other without custom mapping. The moment teams invent their own ad-hoc keys, that shared understanding breaks and every tool needs special-casing.

So the convention is a small habit with a large payoff. Reaching for the standard attribute name instead of making one up, and setting the standard resource attributes everywhere, costs almost nothing at the time of writing. In return you get telemetry that is portable across tools and easy to query, which is the whole point of adopting a common standard.

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
