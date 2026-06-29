# Fluentd — inputs, filters, outputs

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Source directives](#1-source-directives)
  * [2. Filter directives](#2-filter-directives)
  * [3. Match directives](#3-match-directives)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Fluentd configuration is built from directives that form a pipeline. A `source` defines an input — tailing files, receiving forward or syslog traffic, HTTP — and stamps each event with a tag; `filter` directives transform or enrich matching events; and `match` directives send matching events to outputs.

Events therefore enter through sources, are shaped by filters, and leave through matches, all selected by tag. This source-filter-match structure is the whole configuration model.

---

## Detailed explanation with examples

### 1. Source directives

- TODO: `<source>` (tail, forward, syslog, http); sets the tag

### 2. Filter directives

- TODO: `<filter>` (record_transformer, parser, grep)

### 3. Match directives

- TODO: `<match>` to outputs

### 4. Practical rule

```text
source sets the tag; filter shapes; match outputs — all by tag.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep filters minimal; parse/normalize close to the source

### Operations and production

- TODO: order match rules carefully; ensure no event is unmatched

## References

- Official docs: https://docs.fluentd.org/configuration
- Overview: [fundamentals.md](fundamentals.md)
- Related: [tags-and-routing.md](tags-and-routing.md)
