# Documentation rules

## Structure

Every tool section should start from [tool-readme-template.md](templates/tool-readme-template.md) and grow dedicated pages as needed.

Recommended page set:

1. **README** — summary, use cases, links
2. **Architecture** — components, data flow, dependencies
3. **Deployment** — install paths and minimal viable setup
4. **Operations** — upgrades, scaling, backup, monitoring
5. **Troubleshooting** — symptoms → causes → fixes
6. **Production checklist** — go-live and ongoing review items

## Writing style

- Lead with the decision or task, not history.
- Use short paragraphs and bullet lists for scanability.
- Show real config snippets; mark placeholders clearly (`<REDACTED>`, `<env-var>`).
- State assumptions (environment, scale, version).
- Call out breaking changes and version-specific behavior.

## Code and commands

- Prefer copy-pasteable blocks with language tags.
- Include expected output or success criteria when helpful.
- Never commit secrets, tokens, or private keys.

## Diagrams

- Use ASCII or Mermaid for architecture sketches.
- Keep diagrams focused; split complex systems across multiple figures.

## Maintenance

- Date major revisions in commit messages, not inline unless versioning a guide.
- Link to upstream release notes when documenting upgrades.
- Remove or update stale instructions rather than appending contradictory notes.

## Review checklist

- [ ] Accurate for stated version or version range
- [ ] Links work (relative paths)
- [ ] Commands tested or clearly marked as illustrative
- [ ] Security implications noted (TLS, auth, network exposure)
- [ ] Fits [naming conventions](naming-conventions.md)
