# Agent Relay GitHub Mode Layout

## Minimal Mapping

- Active program -> one GitHub Issue
- Goal and acceptance criteria -> issue body
- Current status -> labels or project fields
- Trusted best / benchmark provenance -> issue section or pinned comment
- Handoff -> latest issue comment with `## HANDOFF`
- Scope / write boundaries -> issue body section or pinned comment

## Good Defaults

- Use one active issue per program.
- Keep a consistent issue title format such as `P-2026-001: x4 ASRF benchmark mainline`.
- Use labels for high-level state, such as:
  - `relay:active`
  - `relay:blocked`
  - `relay:review`
- Reserve handoff details for comments so the issue body stays readable.

## Recommended Pairing

- Use `$agent-relay-github-handoff` to resume from issue/project state.
- Use `$agent-relay-github-update` to refresh issue comments and trusted-best notes manually.
