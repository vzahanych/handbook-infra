# Fluentd — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The unified logging layer](#1-the-unified-logging-layer)
  * [2. Inputs, filters, outputs](#2-inputs-filters-outputs)
  * [3. Tags and routing](#3-tags-and-routing)
  * [4. Buffering and reliability](#4-buffering-and-reliability)
  * [5. Plugins](#5-plugins)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Fluentd is a log collector and aggregator built to be a "unified logging layer" — a single place that ingests data from many sources, normalizes it, and routes it to many destinations. Written in Ruby with a C core, it is heavier than Fluent Bit but has a vast plugin ecosystem, which makes it the usual choice for the central aggregation role rather than the per-node edge.

Its model is event-based: each event has a tag, a timestamp, and a record, and configuration is a set of source, filter, and match directives that route events by tag. Buffering with retries gives reliable delivery, and hundreds of plugins connect almost any input to almost any output. Thinking in tagged events flowing through match rules is the key to Fluentd.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. The unified logging layer

Decoupling producers from consumers through one central layer. See [the-unified-logging-layer.md](the-unified-logging-layer.md).

### 2. Inputs, filters, outputs

The source / filter / match directive pipeline. See [inputs-filters-outputs.md](inputs-filters-outputs.md).

### 3. Tags and routing

Tag-driven routing through filter and match patterns. See [tags-and-routing.md](tags-and-routing.md).

### 4. Buffering and reliability

Memory/file buffers, chunks, retries, and dead-letter. See [buffering-and-reliability.md](buffering-and-reliability.md).

### 5. Plugins

The plugin ecosystem that connects any source to any sink. See [plugins.md](plugins.md).

### 6. Practical rule

```text
Events are tagged; config is source → filter → match by tag.
Use file buffers + retries for reliable delivery; lean on plugins for any sink.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: design a coherent tag scheme; keep filters lean
- TODO: normalize records early so outputs see consistent fields

### Operations and production

- TODO: use file buffers + tuned retry/flush for durability; configure secondary/dead-letter
- TODO: pin plugin versions; monitor buffer queue length and retries

## References

- Official docs: https://docs.fluentd.org/
- Related: [../fluent-bit/fundamentals.md](../fluent-bit/fundamentals.md)
