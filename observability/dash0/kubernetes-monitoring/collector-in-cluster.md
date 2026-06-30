# Dash0 Kubernetes monitoring — the in-cluster Collector

## Core idea

Kubernetes monitoring is anchored by an OpenTelemetry Collector deployed inside the cluster, usually as a DaemonSet for node-local data plus a deployment for cluster-wide metrics. It scrapes the kubelet, the Kubernetes API, and container runtimes, enriches every signal with k8s resource attributes, and exports OTLP to Dash0. Running collection in-cluster is what gives the telemetry its Kubernetes identity before it ever leaves the cluster.

---

## References

- Official site: https://www.dash0.com
- Related: [../opentelemetry-native/collector-and-sdks.md](../opentelemetry-native/collector-and-sdks.md)
