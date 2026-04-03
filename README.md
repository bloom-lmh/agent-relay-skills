# Agent Relay Skills

✨ Reusable local-mode and GitHub-mode relay skills for Codex-style agents.

Agent Relay Skills turns the ideas in [yan5xu/code-relay](https://github.com/yan5xu/code-relay) into a practical, shareable skill collection for resumable agent work.

[中文说明](./README_CN.md)

This repository packages and generalizes that article's core ideas:

- externalize working context
- keep resumable handoff artifacts outside chat history
- separate setup, read-only resume, and manual handoff refresh
- support both local-file mode and GitHub-native mode

The goal is not to replace the original project. The goal is to provide a clean implementation and wrapper that other repositories and teams can reuse quickly.

## Quick Pitch

- Build relay workflows once
- Resume work from docs instead of chat history
- Separate setup, resume, and manual update
- Support both local file workflows and GitHub-native workflows

## Included Skills

### Local Mode

- `agent-relay-local-setup`: scaffold or refresh a local code relay workflow
- `agent-relay-local-handoff`: resume a repository from `AGENTS.md` and relay docs
- `agent-relay-local-update`: force-refresh `STATUS`, `CHECKPOINT`, `HANDOFF`, and optional `LEADERBOARD`

### GitHub Mode

- `agent-relay-github-setup`: map code relay onto Issues, Projects, labels, and comments
- `agent-relay-github-handoff`: resume work from an active relay issue and handoff comments
- `agent-relay-github-update`: force-refresh the GitHub relay issue and handoff state

## Naming Convention

This collection uses a normalized naming scheme:

- `agent-relay-local-*`
- `agent-relay-github-*`

The split is intentional:

- `setup`
  - create or refresh the relay structure
- `handoff`
  - read and resume from relay state
- `update`
  - write and refresh relay state manually

## Why Split Handoff and Update

The read path and write path are different:

- `handoff` is safe, document-driven, and can work in read-only situations
- `update` is the explicit write skill for keeping relay docs or GitHub relay state current

This makes the workflow easier to teach and easier to adopt across teams.

## Recommended Usage

### Local repositories

1. Use `$agent-relay-local-setup`
2. Resume work with `$agent-relay-local-handoff`
3. Refresh state manually with `$agent-relay-local-update`

### GitHub-tracked repositories

1. Use `$agent-relay-github-setup`
2. Resume work with `$agent-relay-github-handoff`
3. Refresh issue/project handoff state with `$agent-relay-github-update`

## Hook Strategy

When a repository wants automation, choose refresh moments deliberately:

- manual-only
- pre-commit
- post-merge
- post-train

If the workflow needs lifecycle automation and the current session is not in Plan mode, prefer enabling Plan mode first so trigger points are chosen intentionally.

## Repository Layout

```text
skills/
  agent-relay-local-setup/
  agent-relay-local-handoff/
  agent-relay-local-update/
  agent-relay-github-setup/
  agent-relay-github-handoff/
  agent-relay-github-update/
```

## How To Install

Install the whole collection from GitHub:

```bash
npx skills add bloom-lmh/agent-relay-skills
```

Or install from a GitHub URL:

```bash
npx skills add https://github.com/bloom-lmh/agent-relay-skills
```

Install a single skill if your skills tooling supports a per-skill selector:

```bash
npx skills add https://github.com/bloom-lmh/agent-relay-skills --skill agent-relay-local-handoff
```

## Relationship To The Original Article

This repository is an implementation and packaging layer inspired by:

- [yan5xu/code-relay](https://github.com/yan5xu/code-relay)

The original article focuses on the workflow idea.
This repository focuses on reusable skill packaging:

- local mode
- GitHub mode
- standardized naming
- handoff/update separation
- portability across repositories
