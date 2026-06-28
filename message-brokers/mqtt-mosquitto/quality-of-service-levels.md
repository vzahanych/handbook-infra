# MQTT / Mosquitto — quality of service levels

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. QoS 0 at-most-once](#1-qos-0-at-most-once)
  * [2. QoS 1 at-least-once](#2-qos-1-at-least-once)
  * [3. QoS 2 exactly-once](#3-qos-2-exactly-once)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

MQTT offers three quality-of-service levels that trade delivery certainty against overhead, chosen per message and per subscription. QoS 0 is at-most-once, fire-and-forget with no acknowledgement, fine for frequent disposable readings. QoS 1 is at-least-once, where the broker resends until acknowledged, so messages arrive but may duplicate. QoS 2 is exactly-once, using a four-step handshake that guarantees no loss and no duplication at the highest cost.

Picking the lowest QoS that meets the requirement is how you keep constrained devices efficient.

---

## Detailed explanation with examples

### 1. QoS 0 at-most-once

- TODO: no ack; may be lost; cheapest

### 2. QoS 1 at-least-once

- TODO: resend until PUBACK; possible duplicates

### 3. QoS 2 exactly-once

- TODO: four-step handshake; no loss/dup; most overhead

### 4. Practical rule

```text
QoS 0 for disposable telemetry, QoS 1 for important data (idempotent consumers),
QoS 2 only when duplicates are unacceptable.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: default to the lowest acceptable QoS; make QoS 1 consumers idempotent

### Operations and production

- TODO: watch in-flight QoS 1/2 message buildup on slow links

## References

- Official docs: https://mosquitto.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
