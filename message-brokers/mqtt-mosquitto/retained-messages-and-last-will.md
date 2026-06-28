# MQTT / Mosquitto — retained messages and last will

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Retained messages](#1-retained-messages)
  * [2. Last will and testament](#2-last-will-and-testament)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Two MQTT features address the fact that subscribers come and go. A retained message is the last message the broker keeps for a topic, delivered immediately to any new subscriber, so a device that just connected learns the current state — say a switch's on/off — without waiting for the next publish.

The last will and testament is a message a client registers at connect time that the broker publishes automatically if that client disconnects unexpectedly, which is how the system detects and announces dead devices. Together they make state and presence observable despite intermittent connections.

---

## Detailed explanation with examples

### 1. Retained messages

- TODO: retain flag; new subscribers get the last value
- TODO: clearing a retained message (empty payload)

### 2. Last will and testament

- TODO: LWT registered at connect; published on unexpected disconnect
- TODO: presence/online-offline patterns

### 3. Practical rule

```text
Use retained messages for current state; LWT for presence/death detection.
Clear retained state by publishing an empty retained payload.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: publish state as retained; register an LWT on every device connection

### Operations and production

- TODO: watch retained-message sprawl; reconcile presence via LWT + keepalive

## References

- Official docs: https://mosquitto.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
