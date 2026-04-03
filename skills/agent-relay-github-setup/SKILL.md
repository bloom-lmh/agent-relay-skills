---
name: agent-relay-github-setup
description: Set up or refresh a GitHub-native code relay workflow that stores active program state in GitHub Issues, Projects, labels, and handoff comments instead of local repository files. Use when Codex should adapt code relay for teams who manage tasks through GitHub and want resumable relay state without depending on local-only orchestrator files.
---

# Agent Relay GitHub Setup

## Overview

Use this skill to package code relay concepts into GitHub-native artifacts such as issue bodies, project fields, labels, comments, and optional repository docs.
Pair it with [$agent-relay-github-handoff](../agent-relay-github-handoff/SKILL.md) for resume and read-only recovery, and [$agent-relay-github-update](../agent-relay-github-update/SKILL.md) for manual refresh.

## Workflow

1. Inspect the repository's current GitHub workflow:
   - issues
   - pull requests
   - projects
   - labels
   - issue templates or contributing docs
2. Choose a relay mapping:
   - one active issue per program
   - issue body for goal and acceptance criteria
   - labels or project fields for status
   - issue comments for handoff blocks
   - optional repository docs for global rules
3. Define the minimum standard needed:
   - active-program naming
   - trusted-best section
   - handoff comment format
   - scope or write-boundary note
4. Choose update moments:
   - manual-only
   - before PR / before commit summary
   - after merge
   - after training or benchmark completion
5. If the user wants lifecycle automation and the current session is not in Plan mode, recommend enabling Plan mode before selecting the trigger strategy.

## Suggested Mapping

- `PROGRAM.md` -> active GitHub Issue body
- `STATUS.yml` -> Project fields, labels, or structured status section in the issue body
- `CHECKPOINT.md` -> issue section or pinned trusted-best comment
- `HANDOFF.md` -> latest issue comment with a clear `## HANDOFF` heading
- `LEADERBOARD.md` -> optional repository doc or pinned issue comment
- `SCOPE.yml` -> issue body section, pinned comment, or repository policy doc

## Execution Rules

- Keep the GitHub relay convention lightweight.
- Prefer a single active issue per program unless the user explicitly wants multiple parallel tracks.
- Keep the handoff format copyable and easy to update by humans.
- If the repository already uses local relay files and the user wants to keep them, document the bridge instead of forcing a full migration.

## References

See [references/github-mode-layout.md](./references/github-mode-layout.md) for a compact mapping and usage notes.
