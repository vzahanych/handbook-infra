# OpenTelemetry — resource detectors

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. What a resource is](#1-what-a-resource-is)
  * [2. What detectors discover](#2-what-detectors-discover)
  * [3. Merge order and overrides](#3-merge-order-and-overrides)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Resource detectors are the components that fill in where your telemetry came from. They do this by inspecting the environment your application runs in when it starts up, and recording what they find as resource attributes. The point is to discover the origin of the data automatically rather than make you write it down by hand.

To understand them you first need the idea of a resource. A resource is the fixed set of attributes that describes the entity producing telemetry, such as the service name and version, the host and operating system, the process, and the cloud or Kubernetes details around it. Once established it is attached to every signal the application emits, so every span, metric, and log knows its source.

A detector is what populates that resource. One detector reads attributes from environment variables, another reads process and operating-system facts, and others query the container runtime or a cloud provider's metadata endpoint to learn the region, account, or pod. Each contributes the slice of the picture it knows about.

Because several detectors can run at once, their findings are merged, and there are clear rules for what wins when they overlap. Values you set explicitly, including anything supplied through the standard resource-attributes environment variable, take precedence over what is detected, so you can always override a guess. The result is one combined resource assembled from many sources.

All of this matters because telemetry is only useful when you can tell where it came from, and that origin is a property of the deployment rather than the code. Detectors keep the resource accurate as the very same binary moves from a laptop to a build runner to a production pod. With that origin in place, a backend can group and filter by service, version, host, and environment without anyone tagging the data manually.

---

## Detailed explanation with examples

### 1. What a resource is

- TODO: immutable attributes (service.name/version, host, os, process, cloud, k8s) on every signal

### 2. What detectors discover

- TODO: env-var detector, process/OS detectors, container, cloud (AWS/GCP/Azure), Kubernetes

### 3. Merge order and overrides

- TODO: how multiple detectors combine; explicit attrs vs detected; OTEL_RESOURCE_ATTRIBUTES

### 4. Practical rule

```text
Let detectors fill the resource; always set service.name yourself.
Accurate origin attributes are what make telemetry groupable.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: enable platform detectors for the deploy target; set service.name/version explicitly

### Operations and production

- TODO: verify resource attrs in the backend; avoid high-cardinality custom resource keys

## References

- Official docs: https://opentelemetry.io/docs/concepts/resources/
- Components overview: https://opentelemetry.io/docs/concepts/components/
- Related: [concept-semantic-conventions.md](concept-semantic-conventions.md)
- Overview: [fundamentals.md](fundamentals.md)
