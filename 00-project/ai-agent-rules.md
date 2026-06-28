# AI agent rules

Guidance for AI-assisted authoring in this repository.

## Before writing

1. Read [goals.md](goals.md), [documentation-rules.md](documentation-rules.md), and [naming-conventions.md](naming-conventions.md).
2. Use the appropriate template from [templates/](templates/).
3. Search existing sections for patterns; match tone and structure.

## When adding a tool section

- Create or update the tool directory under the correct category.
- Add an entry to [CONTENTS.md](../CONTENTS.md) if missing.
- Start with `README.md`; add other pages only when there is substantive content.
- Prefer linking to official documentation for exhaustive API references.

## Content quality

- Do not invent version numbers, flags, or defaults — verify or mark as TBD.
- Distinguish opinion from fact; label recommendations clearly.
- Include trade-offs and alternatives where choices exist.
- Avoid filler, repetition, and generic DevOps platitudes.

## Safety

- Never generate or embed real credentials.
- Flag destructive commands (`rm`, `drop`, `delete`, force flags).
- Note blast radius for production-impacting operations.

## Scope control

- One logical change per task (one tool page, one template update, one lab).
- Do not refactor unrelated sections.
- Do not create empty placeholder pages across the entire tree — expand incrementally.
