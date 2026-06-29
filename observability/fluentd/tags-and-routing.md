# Fluentd — tags and routing

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Tags on events](#1-tags-on-events)
  * [2. Tag patterns](#2-tag-patterns)
  * [3. Rewriting tags](#3-rewriting-tags)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Routing in Fluentd is driven entirely by tags. Every event carries a tag assigned at its source, and `filter` and `match` directives specify a tag pattern — exact, wildcard, or alternation — that decides which events they handle. Events flow top-to-bottom through the config, matched by the first applicable rule.

Tags can be rewritten to redirect events through different paths. Designing a coherent tagging scheme is what makes a Fluentd configuration predictable and maintainable.

---

## Detailed explanation with examples

### 1. Tags on events

- TODO: tag set at source; dotted hierarchy convention

### 2. Tag patterns

- TODO: `*`, `**`, `{a,b}` matching; first-match wins

### 3. Rewriting tags

- TODO: rewrite_tag_filter / relabel to redirect

### 4. Practical rule

```text
Design a dotted tag hierarchy; remember first matching <match> wins.
Use relabel/rewrite to redirect rather than duplicating rules.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: consistent tag namespace; avoid overlapping greedy `**`

### Operations and production

- TODO: add a catch-all match to surface unrouted events

## References

- Official docs: https://docs.fluentd.org/configuration/routing-examples
- Overview: [fundamentals.md](fundamentals.md)
