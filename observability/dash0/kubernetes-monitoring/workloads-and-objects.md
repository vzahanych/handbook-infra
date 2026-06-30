# Dash0 Kubernetes monitoring — workloads and objects

## Core idea

The signals are organized around Kubernetes objects — namespaces, deployments, replica sets, pods, and containers — rather than raw hosts, so the view matches how teams operate the cluster. Resource attributes like k8s.namespace.name and k8s.pod.name let Dash0 roll telemetry up a workload's hierarchy and filter down to a single container. Reasoning in object terms is what makes "which deployment is failing?" a direct question instead of a manual mapping exercise.

---

## References

- Official site: https://www.dash0.com
- Related: [../opentelemetry-native/semantic-conventions.md](../opentelemetry-native/semantic-conventions.md)
