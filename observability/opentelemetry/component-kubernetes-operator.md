# OpenTelemetry — Kubernetes operator

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Managing the Collector](#1-managing-the-collector)
  * [2. Auto-instrumentation injection](#2-auto-instrumentation-injection)
  * [3. Deployment modes](#3-deployment-modes)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

The OpenTelemetry Operator brings OpenTelemetry into Kubernetes the way Kubernetes itself likes to work, through declarative custom resources. Instead of running and wiring things by hand, you describe what you want in a manifest and the operator continuously makes the cluster match it. It manages two things in particular: the collector, and the automatic instrumentation of your workloads.

Managing the collector is the first half. You write a resource that describes the collector you want, including its configuration and how it should be deployed, and the operator creates and maintains it for you. If the configuration drifts or a pod dies, the operator reconciles the cluster back to the state you declared.

Injecting instrumentation is the second and more distinctive half. You write a separate resource that names a language and its settings, and then you annotate the pods that should receive it. When such a pod is created, the operator steps in through an admission webhook and adds the zero-code agent, the exporter endpoint, and the resource attributes, all without rebuilding the application image.

It is also flexible about how the collector itself is deployed. The same operator can run a collector as a central deployment, as a node-level daemon that collects from every host, as a sidecar beside a single workload, or as a stateful set when persistence matters. You pick the shape that fits the job rather than being forced into one.

Taken together, this is what makes telemetry feel native to the cluster. The plumbing is configured with the same manifests, the same review process, and the same tooling as everything else you run on Kubernetes. A common arrangement pairs a node-level agent for collection with a central gateway for processing, and instruments the workloads themselves simply by annotating their pods.

---

## Detailed explanation with examples

### 1. Managing the Collector

- TODO: OpenTelemetryCollector CR; operator reconciles deployment/config

### 2. Auto-instrumentation injection

- TODO: Instrumentation CR + pod annotation; admission webhook injects agent and env

### 3. Deployment modes

- TODO: Collector as deployment, daemonset, sidecar, statefulset

### 4. Practical rule

```text
Run the Collector and inject zero-code instrumentation via CRs.
Annotate pods to instrument them without rebuilding images.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use the Instrumentation CR for injection; set exporter endpoint to the in-cluster Collector

### Operations and production

- TODO: pick Collector mode per need (daemonset agent + deployment gateway); pin operator version

## References

- Official docs: https://opentelemetry.io/docs/platforms/kubernetes/operator/
- Components overview: https://opentelemetry.io/docs/concepts/components/
- Related: [component-collector.md](component-collector.md), [component-zero-code-instrumentation.md](component-zero-code-instrumentation.md)
- Overview: [fundamentals.md](fundamentals.md)
