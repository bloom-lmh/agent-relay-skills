# Agent Relay Local Layout

## Minimal File Set

```text
AGENTS.md
orchestrator/
  ALWAYS/
    BOOT.md
    CORE.md
    DEV-FLOW.md
    SUB-AGENT.md
    RESOURCE-MAP.yml
  PROGRAMS/
    P-YYYY-001/
      PROGRAM.md
      STATUS.yml
      SCOPE.yml
      workspace/
        CHECKPOINT.md
        HANDOFF.md
        LEADERBOARD.md
```

## File Roles

- `AGENTS.md`
  - top-level entry point
  - tells Codex what to read first
- `BOOT.md`
  - fixed restore order
- `CORE.md`
  - global constraints and trusted baseline
- `DEV-FLOW.md`
  - working loop and update discipline
- `RESOURCE-MAP.yml`
  - repository map, infrastructure, artifacts, and relationships
- `PROGRAM.md`
  - objective and acceptance criteria for the active task
- `STATUS.yml`
  - current state, best known result, done/doing/next
- `SCOPE.yml`
  - write boundaries
- `CHECKPOINT.md`
  - trusted best results, ruled-out lines, experiment provenance
- `HANDOFF.md`
  - end-of-session summary and next recommended action
- `LEADERBOARD.md`
  - optional ranking view of best runs

## Recommended Pairing

- Use `$agent-relay-local-handoff` to resume a repository from relay docs.
- Use `$agent-relay-local-update` to force-refresh relay docs when hooks are absent or skipped.
- If the user asks for lifecycle automation and the session is not in Plan mode, recommend Plan mode before choosing trigger points.
