# Dash0 observability as code — GitOps workflow

## Core idea

The GitOps workflow stores dashboards and alert definitions in version control and applies them through the same pipelines that ship application code. Treating monitoring config as reviewable, versioned artifacts brings change history, code review, and rollback to observability. Tying these updates to application releases is what prevents the common drift where the running system evolves but its dashboards and alerts quietly fall behind.

---

## References

- Official site: https://www.dash0.com
- Related: [../dashboards/import-export-portability.md](../dashboards/import-export-portability.md)
