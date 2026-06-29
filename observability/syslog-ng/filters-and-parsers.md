# syslog-ng — filters and parsers

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Filters for routing](#1-filters-for-routing)
  * [2. Parsers for structure](#2-parsers-for-structure)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Between source and destination, syslog-ng can filter and parse messages to control what goes where and to add structure. Filters select messages by facility, severity, host, program, or message content, so a log path can route only error-level auth messages to one destination, for example.

Parsers extract structure from message text — splitting key-value pairs, parsing JSON, or applying patterns — turning a flat line into named fields that destinations and later filters can use. Combining filters for routing with parsers for structure is how you turn raw syslog into organized, queryable output.

---

## Detailed explanation with examples

### 1. Filters for routing

- TODO: `filter { facility(...) and level(...) }`; host/program/match

### 2. Parsers for structure

- TODO: kv-parser, json-parser, PatternDB; named-value pairs

### 3. Practical rule

```text
Filter to route; parse to add structure (kv/json) for downstream use.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: parse into named values; route with precise filters

### Operations and production

- TODO: test filters/parsers on samples; watch parser failure rates

## References

- Official docs: https://www.syslog-ng.com/technical-documents/
- Overview: [fundamentals.md](fundamentals.md)
