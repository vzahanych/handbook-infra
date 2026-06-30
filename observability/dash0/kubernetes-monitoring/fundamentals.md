# Dash0 Kubernetes monitoring — fundamentals

## Core idea

Kubernetes monitoring is Dash0's dedicated observability for containerized environments, built around an OpenTelemetry Collector running in the cluster to gather pod, node, workload, and control-plane signals. It maps raw telemetry onto Kubernetes objects — namespaces, deployments, pods, containers — so you reason about health in cluster terms rather than anonymous hosts. That Kubernetes-aware model also underpins observability-as-code, letting dashboards and alerts ship alongside the manifests they describe.

---

## Cards in this folder

- [collector-in-cluster.md](collector-in-cluster.md) — how the in-cluster Collector gathers signals.
- [workloads-and-objects.md](workloads-and-objects.md) — mapping telemetry to Kubernetes objects.
- [control-plane-and-nodes.md](control-plane-and-nodes.md) — node and control-plane health.

---

## References

- Official site: https://www.dash0.com
- Related: [../infrastructure-monitoring/fundamentals.md](../infrastructure-monitoring/fundamentals.md), [../../../orchestration/kubernetes/](../../../orchestration/kubernetes/)
