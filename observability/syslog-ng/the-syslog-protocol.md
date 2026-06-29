# syslog-ng — the syslog protocol

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Facility and severity](#1-facility-and-severity)
  * [2. Message formats](#2-message-formats)
  * [3. Transports](#3-transports)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

syslog is the long-standing standard for system logging, and understanding it grounds how syslog-ng works. A syslog message carries a facility (what subsystem produced it, like auth or cron) and a severity (how important, from debug to emergency), along with a timestamp, host, and the message text.

Two main wire formats exist: the older BSD format (RFC 3164) and the newer structured format (RFC 5424), and messages travel over UDP, TCP, or TLS. syslog-ng speaks all of these, which is why it interoperates with the huge range of devices and systems that emit syslog.

---

## Detailed explanation with examples

### 1. Facility and severity

- TODO: facilities (auth, cron, local0-7); severities (debug→emerg)

### 2. Message formats

- TODO: RFC 3164 (BSD) vs RFC 5424 (structured data)

### 3. Transports

- TODO: UDP (lossy) vs TCP vs TLS

### 4. Practical rule

```text
Route by facility/severity; prefer RFC 5424 + TCP/TLS over BSD/UDP.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use structured RFC 5424 where producers support it

### Operations and production

- TODO: avoid UDP for important logs (silent loss); use TLS over untrusted networks

## References

- Official docs: https://www.syslog-ng.com/technical-documents/
- Overview: [fundamentals.md](fundamentals.md)
