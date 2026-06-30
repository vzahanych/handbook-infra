# Dash0 website monitoring — frontend errors

## Core idea

Frontend error capture records client-side failures — JavaScript exceptions and failed requests — as they happen in users' browsers. These surface problems that never reach a server log, like a broken bundle or a failing third-party script, which would otherwise be invisible to backend monitoring. Tied to the session and the backend calls around them, a frontend error becomes a starting point for a full-stack investigation rather than an isolated report.

---

## References

- Official site: https://www.dash0.com
- Related: [front-to-back-correlation.md](front-to-back-correlation.md)
