# Dash0 Kubernetes monitoring — control plane and nodes

## Core idea

Beyond workloads, Kubernetes monitoring covers the substrate the cluster runs on: node resource pressure and the control-plane components that schedule and manage work. Node CPU, memory, and disk pressure explain pod evictions and scheduling failures, while control-plane and kubelet signals reveal cluster-level health problems. Watching this layer is what lets you tell an application bug apart from the cluster running out of capacity beneath it.

---

## References

- Official site: https://www.dash0.com
- Related: [../infrastructure-monitoring/metrics-and-signals.md](../infrastructure-monitoring/metrics-and-signals.md)
