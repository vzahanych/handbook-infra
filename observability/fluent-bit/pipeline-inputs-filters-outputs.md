# Fluent Bit — pipeline: inputs, filters, outputs

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Inputs](#1-inputs)
  * [2. Filters](#2-filters)
  * [3. Outputs](#3-outputs)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Fluent Bit processes data as a pipeline with four stages: inputs read records from sources, parsers turn raw text into structured fields, filters modify or enrich records, and outputs send them to destinations. Inputs cover files, syslog, systemd, and many others; outputs cover Elasticsearch, Loki, Kafka, S3, and more.

Each record flows from an input, optionally through filters, to one or more outputs chosen by routing. This staged design is what makes the agent both composable and fast.

---

## Detailed explanation with examples

### 1. Inputs

- TODO: tail (files), systemd, syslog, forward; each input sets a tag

### 2. Filters

- TODO: modify/enrich (kubernetes, modify, grep, lua)

### 3. Outputs

- TODO: Elasticsearch, Loki, Kafka, S3, forward

### 4. Practical rule

```text
Compose input → filter → output stages; keep filters cheap.
Enrich with the kubernetes filter for pod/namespace metadata.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: minimize filter work; enrich with k8s metadata at the edge

### Operations and production

- TODO: prefer the `forward` output to a central aggregator when fanning out

## References

- Official docs: https://docs.fluentbit.io/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [parsers.md](parsers.md)
