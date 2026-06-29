# Fluent Bit — parsers

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Parser types](#1-parser-types)
  * [2. Attaching parsers](#2-attaching-parsers)
  * [3. Parse early](#3-parse-early)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Parsers in Fluent Bit turn an unstructured log line into structured fields, which is what makes downstream filtering and querying possible. You define parsers — regular expressions, JSON, logfmt, or built-in formats — and attach them to inputs so that, say, an Nginx access line becomes fields like method, path, and status.

Parsing early in the pipeline means later filters and the destination see clean structured data rather than raw text. Getting parsers right is most of turning messy logs into useful records.

---

## Detailed explanation with examples

### 1. Parser types

- TODO: regex, json, logfmt, ltsv; built-in parsers

### 2. Attaching parsers

- TODO: parser on the input; multiline parsers for stack traces

### 3. Parse early

- TODO: structure before filters/outputs

### 4. Practical rule

```text
Parse raw lines into fields as early as possible.
Use multiline parsers for stack traces; prefer JSON logs at the source.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: log JSON at the source when possible; keep regex parsers anchored/tested

### Operations and production

- TODO: watch parser failures; avoid catastrophic regex on hot paths

## References

- Official docs: https://docs.fluentbit.io/manual/pipeline/parsers
- Overview: [fundamentals.md](fundamentals.md)
