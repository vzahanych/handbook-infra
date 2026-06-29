# Fluentd — plugins

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Plugin types](#1-plugin-types)
  * [2. Installing plugins](#2-installing-plugins)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Fluentd's defining strength is its plugin ecosystem, with hundreds of community and official plugins for inputs, outputs, filters, parsers, and buffers. This is why it can act as the universal aggregator: there is almost certainly a plugin for any source or destination you need, from cloud storage and search engines to message queues and SaaS APIs.

Plugins are installed as Ruby gems and configured with the same directive syntax as the core. Knowing that capability comes from plugins explains both Fluentd's flexibility and its heavier footprint compared to Fluent Bit.

---

## Detailed explanation with examples

### 1. Plugin types

- TODO: input, output, filter, parser, formatter, buffer

### 2. Installing plugins

- TODO: `fluent-gem install`; bundled vs community

### 3. Practical rule

```text
Reach for a plugin for any source/sink; pin versions for stability.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: prefer well-maintained official plugins

### Operations and production

- TODO: pin plugin/gem versions; test upgrades; watch memory of heavy plugins

## References

- Official docs: https://docs.fluentd.org/plugin-development
- Overview: [fundamentals.md](fundamentals.md)
