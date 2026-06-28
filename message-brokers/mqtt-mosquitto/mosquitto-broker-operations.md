# MQTT / Mosquitto — Mosquitto broker operations

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Configuration and listeners](#1-configuration-and-listeners)
  * [2. TLS, auth, and ACLs](#2-tls-auth-and-acls)
  * [3. Bridging and scaling](#3-bridging-and-scaling)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Mosquitto is the widely used open-source MQTT broker, a small, single-process server suitable from a Raspberry Pi to a production gateway. Operating it centers on its configuration file, where you set listeners and ports, enable TLS, and configure authentication and access-control lists that restrict which clients may publish or subscribe to which topics.

Because MQTT is often exposed to many devices over networks, securing it — TLS, real credentials, and per-topic ACLs — is the primary concern. For scale and high availability, brokers can be bridged together or run in clustered distributions.

---

## Detailed explanation with examples

### 1. Configuration and listeners

- TODO: `mosquitto.conf`; listeners, ports, WebSockets

### 2. TLS, auth, and ACLs

- TODO: TLS certs; password file / auth plugins; per-topic ACLs

### 3. Bridging and scaling

- TODO: broker bridges; clustered distributions for HA

### 4. Practical rule

```text
Never run open: require TLS, real credentials, and per-topic ACLs.
Use bridging/clustered builds for scale and HA.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: scope device credentials to least-privilege topic ACLs

### Operations and production

- TODO: enforce TLS + auth; back up config; monitor connections and resource use

## References

- Official docs: https://mosquitto.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
