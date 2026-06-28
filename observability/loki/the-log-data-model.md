# Loki — the log data model

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Entries and streams](#1-entries-and-streams)
  * [2. Content is not indexed](#2-content-is-not-indexed)
  * [3. Select then scan](#3-select-then-scan)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

A log entry in Loki is just a timestamp and a line of text, grouped into streams. A stream is the unit Loki indexes, and it is defined by a unique set of labels, so all log lines sharing the same labels form one ordered stream.

Crucially, the content of the log line is not indexed — only the labels are — so finding logs is a two-step process: select streams by label, then scan their lines. This is the opposite of a search engine and is why Loki is cheap but rewards good labelling.

---

## Detailed explanation with examples

### 1. Entries and streams

- TODO: entry = timestamp + line; stream = unique label set

### 2. Content is not indexed

- TODO: only labels indexed; lines stored compressed

### 3. Select then scan

- TODO: select streams by label, then scan lines

### 4. Practical rule

```text
A stream = one label set. Loki indexes labels, not log text.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep the number of streams bounded via label design

### Operations and production

- TODO: monitor active stream count

## References

- Official docs: https://grafana.com/docs/loki/latest/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [labels-and-streams.md](labels-and-streams.md)
