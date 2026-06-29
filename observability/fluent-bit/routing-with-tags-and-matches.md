# Fluent Bit — routing with tags and matches

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Tags on records](#1-tags-on-records)
  * [2. Match patterns](#2-match-patterns)
  * [3. Fan-out and splitting](#3-fan-out-and-splitting)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Routing in Fluent Bit is tag-based: every record gets a tag, usually set by its input, and each output declares a match pattern that selects which tags it receives. A record is sent to every output whose match — an exact string or a wildcard like `kube.*` — fits its tag, so one stream can fan out to several destinations or be split by source.

Filters likewise use match patterns to choose which records they act on. Designing a clear tagging scheme is what makes routing predictable.

---

## Detailed explanation with examples

### 1. Tags on records

- TODO: input assigns tag; rewrite_tag filter

### 2. Match patterns

- TODO: exact and wildcard (`Match kube.*`)

### 3. Fan-out and splitting

- TODO: one tag → many outputs; split by tag

### 4. Practical rule

```text
Tag at the input; route with explicit Match patterns.
A clear tag scheme makes fan-out and filtering predictable.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: design a consistent tag namespace; avoid overlapping `Match *`

### Operations and production

- TODO: verify every record matches an intended output (no silent drops)

## References

- Official docs: https://docs.fluentbit.io/manual/concepts/key-concepts
- Overview: [fundamentals.md](fundamentals.md)
