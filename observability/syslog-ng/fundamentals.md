# syslog-ng — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The syslog protocol](#1-the-syslog-protocol)
  * [2. Sources, destinations, and log paths](#2-sources-destinations-and-log-paths)
  * [3. Filters and parsers](#3-filters-and-parsers)
  * [4. Reliability and disk buffering](#4-reliability-and-disk-buffering)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

syslog-ng is a mature, high-performance log collector built around the syslog protocol but extended far beyond it into a general log-processing engine. It receives log messages from system sources and the network, processes them through filters and parsers, and writes them to files, databases, message queues, or remote collectors. Its long history makes it a common choice for system and network logging, especially where the standard syslog formats matter.

Its configuration model is built from objects — sources, destinations, filters, parsers — that you wire together into log paths, each path describing a flow from where messages come in to where they go out. Reliability features like disk-based buffering let it survive outages without losing messages. Thinking in sources, destinations, and the log paths that connect them is the key to syslog-ng.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. The syslog protocol

Facilities, severities, RFC 3164/5424 formats, and transports. See [the-syslog-protocol.md](the-syslog-protocol.md).

### 2. Sources, destinations, and log paths

The object-and-path configuration model. See [sources-destinations-and-log-paths.md](sources-destinations-and-log-paths.md).

### 3. Filters and parsers

Routing by filter and structuring with parsers. See [filters-and-parsers.md](filters-and-parsers.md).

### 4. Reliability and disk buffering

Disk buffers, flow control, and reliable transport. See [reliability-and-disk-buffering.md](reliability-and-disk-buffering.md).

### 5. Practical rule

```text
Wire sources → (filters/parsers) → destinations as log paths.
Use TCP/TLS + disk buffering so outages don't lose logs.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: route with filters; structure messages with parsers (JSON/kv)
- TODO: prefer RFC 5424 + TLS over legacy BSD/UDP where possible

### Operations and production

- TODO: enable disk buffering and flow control to survive destination outages
- TODO: monitor dropped messages and buffer usage

## References

- Official docs: https://www.syslog-ng.com/technical-documents/
- Related: [../fluentd/fundamentals.md](../fluentd/fundamentals.md)
