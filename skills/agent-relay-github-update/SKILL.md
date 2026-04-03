---
name: agent-relay-github-update
description: Force-refresh GitHub-native relay state by updating the active issue body, trusted-best notes, project status, and handoff comments when a repository uses GitHub as the main code relay surface. Use when Codex should manually update GitHub relay state after code changes, benchmark runs, before switching sessions, or whenever GitHub automation is absent or intentionally skipped.
---

# Agent Relay GitHub Update

## Overview

Use this skill when GitHub is the main relay surface and the user wants a manual refresh of relay state.
This is the write-side companion to [$agent-relay-github-handoff](../agent-relay-github-handoff/SKILL.md).

## Workflow

1. Identify the active relay issue or task container.
2. Read the current issue body, labels, project fields, trusted-best notes, and latest handoff comment.
3. Inspect the current work state:
   - branch
   - latest commit or PR state
   - trusted best
   - branch outcome
4. Update the GitHub relay state:
   - refresh issue sections for trusted best or active branch state
   - update labels or project state when applicable
   - post or replace a `## HANDOFF` comment
5. If GitHub write tooling is unavailable, prepare a ready-to-paste markdown handoff for the user instead of silently failing.

## Execution Rules

- Be explicit when a branch tied or lost.
- Keep issue bodies concise and move session detail into comments.
- Preserve manual notes in issue bodies or comments when they are clearly written by humans.
- If the repository actually uses local relay files instead of GitHub, switch to [$agent-relay-local-update](../agent-relay-local-update/SKILL.md).

## References

See [references/usage.md](./references/usage.md) for example prompts.
