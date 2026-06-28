# Naming conventions

## Directories

- Tool sections live under category folders: `databases/postgresql/`, `message-brokers/kafka/`, etc.
- Use lowercase kebab-case: `docker-compose`, `redis-streams`, `mqtt-mosquitto`.
- One primary tool per directory; variants and operators get subpages, not sibling top-level dirs.

## Files

- Use lowercase kebab-case: `production-checklist.md`, `backup-restore.md`.
- Standard pages per tool (when applicable):
  - `README.md` — entry point and navigation
  - `architecture.md`
  - `deployment.md`
  - `operations.md`
  - `troubleshooting.md`
  - `production-checklist.md`
- Examples and manifests go in `examples/` at repo root or tool-local `examples/` subfolders.

## Headings

- Title case for page titles (`# PostgreSQL`).
- Sentence case for section headings (`## Backup and restore`).
- Keep heading depth shallow: prefer `##` and `###`; avoid skipping levels.

## Links

- Prefer relative links within the repo.
- Link to official docs for API reference details rather than copying them.
