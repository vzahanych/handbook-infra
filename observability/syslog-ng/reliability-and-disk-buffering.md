# syslog-ng — reliability and disk buffering

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Disk buffering](#1-disk-buffering)
  * [2. Flow control](#2-flow-control)
  * [3. Reliable transport](#3-reliable-transport)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

syslog-ng is built to not lose logs, and disk-based buffering is the main reason. When a destination is unreachable — a remote server down or a network partition — syslog-ng can spool messages to a disk buffer and replay them once the destination returns, rather than dropping them as a simple UDP forwarder would.

Flow control similarly slows ingestion when destinations cannot keep up, applying backpressure instead of overflowing memory. Using TCP or TLS transport together with disk buffering is how you build a syslog pipeline that survives outages.

---

## Detailed explanation with examples

### 1. Disk buffering

- TODO: `disk-buffer(...)`; reliable vs normal disk buffers

### 2. Flow control

- TODO: backpressure when destinations lag

### 3. Reliable transport

- TODO: TCP/TLS over UDP for delivery

### 4. Practical rule

```text
Use reliable disk buffers + flow control + TCP/TLS so outages don't lose logs.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: enable disk-buffer on network destinations; choose reliable mode for critical logs

### Operations and production

- TODO: size disk-buffer capacity; monitor buffer usage and dropped messages

## References

- Official docs: https://www.syslog-ng.com/technical-documents/
- Overview: [fundamentals.md](fundamentals.md)
