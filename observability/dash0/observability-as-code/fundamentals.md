# Dash0 observability as code — fundamentals

## Core idea

Observability as code lets teams define and maintain monitoring configuration — dashboards and alert rules — the same way they manage infrastructure and applications, through version control and pipelines rather than manual UI edits. Built on open formats (Perses dashboards, PromQL alerts) plus Kubernetes-native support and an API, configurations become repeatable, reviewable, and automatable, and they update in lockstep with the application releases they describe. This GitOps approach is what keeps monitoring from drifting away from the system it is supposed to watch.

---

## Cards in this folder

- [gitops-workflow.md](gitops-workflow.md) — config in Git, shipped through pipelines.
- [kubernetes-native-and-api.md](kubernetes-native-and-api.md) — the Kubernetes and API surfaces for applying config.

---

## References

- Official site: https://www.dash0.com
- Related: [../dashboards/fundamentals.md](../dashboards/fundamentals.md), [../alerting/fundamentals.md](../alerting/fundamentals.md), [../../../infrastructure-as-code/](../../../infrastructure-as-code/)
