---
name: agent-relay-github-handoff
description: Resume or hand off GitHub-native relay workflows by reading the active issue, project status, labels, trusted-best notes, and the latest handoff comment instead of local orchestrator files. Use when Codex should recover context from GitHub issue/project state and prepare a clean handoff without depending on chat history.
---

# Agent Relay GitHub Handoff

## Overview

Use this skill when the repository manages relay state in GitHub Issues, Projects, and comments rather than local files.

## Workflow

1. Identify the active relay issue or task container.
2. Read:
   - issue title and body
   - labels and project status
   - trusted-best section or pinned benchmark note
   - latest `## HANDOFF` comment or equivalent handoff comment
3. Summarize:
   - current trusted best
   - current doing
   - current next
   - open questions or blockers
4. If GitHub connector or CLI tools are unavailable, prepare a read-only summary from whatever exported issue content the user provided.

## Execution Rules

- Prefer the active issue and its latest handoff comment as the source of truth.
- Surface the trusted best baseline clearly.
- Do not rewrite issue state here; this is the read-side skill.
- If the user wants to update the issue or post a new handoff comment, switch to [$agent-relay-github-update](../agent-relay-github-update/SKILL.md).

## References

See [references/usage.md](./references/usage.md) for example prompts.
