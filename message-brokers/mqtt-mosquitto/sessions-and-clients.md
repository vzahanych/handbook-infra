# MQTT / Mosquitto — sessions and clients

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Client IDs](#1-client-ids)
  * [2. Clean versus persistent sessions](#2-clean-versus-persistent-sessions)
  * [3. Keepalive](#3-keepalive)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Each MQTT client identifies itself with a client ID, and the session holds its subscriptions and any queued messages. A clean session starts fresh and discards state on disconnect, while a persistent session lets the broker retain subscriptions and buffer QoS 1 and 2 messages so a client that reconnects receives what it missed.

This is essential for devices that drop off and return, turning brief disconnects into recoverable gaps rather than data loss. Choosing clean versus persistent sessions, and stable client IDs, is the main client-lifecycle decision.

---

## Detailed explanation with examples

### 1. Client IDs

- TODO: unique stable IDs; collisions disconnect the older client

### 2. Clean versus persistent sessions

- TODO: clean start vs retained subscriptions + queued QoS 1/2

### 3. Keepalive

- TODO: keepalive interval; broker detects dead clients

### 4. Practical rule

```text
Stable client IDs + persistent sessions for devices that reconnect.
Clean sessions for stateless/ephemeral clients.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: assign stable unique client IDs; pick session type by reconnect needs

### Operations and production

- TODO: size queued-message limits for persistent sessions; tune keepalive

## References

- Official docs: https://mosquitto.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
