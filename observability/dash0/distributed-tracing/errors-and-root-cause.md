# Dash0 distributed tracing — errors and root cause

## Core idea

Traces expose where a failure originates rather than just where it surfaces, by marking the erroring span and the chain of calls that led to it. Following the trace down to the deepest failing span separates the true cause from the services that merely propagated the error upward. With logs joined to spans by trace id, that failing span carries its own evidence, which is exactly the context Agent0 uses to reason about root cause.

---

## References

- Official site: https://www.dash0.com
- Related: [../log-management/context-and-correlation.md](../log-management/context-and-correlation.md), [../agent0/root-cause-and-code.md](../agent0/root-cause-and-code.md)
