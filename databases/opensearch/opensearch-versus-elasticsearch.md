# OpenSearch — OpenSearch versus Elasticsearch

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The fork and licensing](#1-the-fork-and-licensing)
  * [2. Bundled features](#2-bundled-features)
  * [3. API and setting differences](#3-api-and-setting-differences)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

OpenSearch was forked from Elasticsearch 7.10 after Elastic changed its license, so the two share a deep common core but have diverged since. The most visible differences are licensing — OpenSearch is Apache 2.0 — and bundled features: OpenSearch ships its Security, Dashboards, Alerting, and k-NN plugins for free, where some Elastic equivalents are paid.

APIs and settings have drifted too, with renames like ILM to ISM, and each project has added features the other lacks. The practical rule is to treat them as compatible for the basics but to verify anything version- or feature-specific against the OpenSearch docs rather than assuming an Elasticsearch behavior holds.

---

## Detailed explanation with examples

### 1. The fork and licensing

- TODO: forked from ES 7.10; Apache 2.0

### 2. Bundled features

- TODO: Security, Dashboards, Alerting, k-NN included

### 3. API and setting differences

- TODO: ILM → ISM; renamed/divergent APIs and settings

### 4. Practical rule

```text
Compatible for the basics; verify version/feature specifics in OpenSearch docs.
Remember ISM (not ILM) and bundled plugins.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: don't assume a specific Elasticsearch version's APIs exist unchanged

### Operations and production

- TODO: configure the bundled Security plugin (TLS, roles); use ISM for lifecycle

## References

- Official docs: https://opensearch.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../elasticsearch/fundamentals.md](../elasticsearch/fundamentals.md)
