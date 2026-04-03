# Agent Relay Skills

Agent Relay Skills is a small, reusable skill collection for turning the ideas in [yan5xu/code-relay](https://github.com/yan5xu/code-relay) into a practical, shareable workflow for Codex-style agents.

This repository packages and generalizes that article's core ideas:

- externalize working context
- keep resumable handoff artifacts outside chat history
- separate setup, read-only resume, and manual handoff refresh
- support both local-file mode and GitHub-native mode

The goal is not to replace the original project. The goal is to provide a clean implementation and wrapper that other repositories and teams can reuse quickly.

## Included Skills

### Local Mode

- `agent-relay-local-setup`
  - scaffold or refresh a local code relay workflow
- `agent-relay-local-handoff`
  - resume a repository from `AGENTS.md` and relay docs
- `agent-relay-local-update`
  - force-refresh `STATUS`, `CHECKPOINT`, `HANDOFF`, and optional `LEADERBOARD`

### GitHub Mode

- `agent-relay-github-setup`
  - map code relay onto Issues, Projects, labels, and comments
- `agent-relay-github-handoff`
  - resume work from an active relay issue and handoff comments
- `agent-relay-github-update`
  - force-refresh the GitHub relay issue and handoff state

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

## How To Publish To skills.sh Community

Based on the public install flow documented by [skills.sh](https://skills.sh/) and its docs, the effective publication path is:

1. Keep the repository public on GitHub.
2. Put each skill in a stable folder with a valid `SKILL.md`.
3. Add `agents/openai.yaml` metadata for better discovery.
4. Validate every skill before publishing.
5. Share the repository URL or `owner/repo` install form.

At the time this repository was prepared, the public docs did not expose a separate manual submission form for community listing. In practice, distribution appears to happen through the GitHub-backed install flow and community discovery around public skill repositories.

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

---

# 中文说明

`Agent Relay Skills` 是一套把 [yan5xu/code-relay](https://github.com/yan5xu/code-relay) 思路做成可复用 skill 的实现集合。

它的目标不是替代原项目，而是把那篇文章里的核心做法封装成更容易传播和复用的技能包，方便别人直接安装和使用。

## 包含的能力

### 本地模式

- `agent-relay-local-setup`
  - 初始化或刷新本地 `code relay`
- `agent-relay-local-handoff`
  - 从 `AGENTS.md` 和交接文档恢复上下文
- `agent-relay-local-update`
  - 手动强制刷新 `STATUS / CHECKPOINT / HANDOFF / LEADERBOARD`

### GitHub 模式

- `agent-relay-github-setup`
  - 把 relay 工作流映射到 GitHub Issues / Projects / comments
- `agent-relay-github-handoff`
  - 从 GitHub relay issue 和交接 comment 恢复上下文
- `agent-relay-github-update`
  - 手动刷新 GitHub 上的 relay 状态

## 命名规范

统一采用：

- `agent-relay-local-*`
- `agent-relay-github-*`

其中：

- `setup` 负责搭结构
- `handoff` 负责读和恢复
- `update` 负责手动刷新

## 为什么要把 handoff 和 update 分开

因为“读取上下文”和“改写交接状态”其实是两件不同的事情：

- `handoff` 更安全，适合只读恢复
- `update` 更适合在没有 hooks 或自动化时手动强制刷新

这样设计更容易教学，也更适合跨团队使用。

## 发布到 skills.sh 社区怎么做

目前更合理的理解是：

1. 把 skill 仓库公开放到 GitHub
2. 保持 `skills/<skill-name>/SKILL.md` 这种稳定结构
3. 为 skill 提供 `agents/openai.yaml`
4. 让别人能通过 GitHub 仓库地址直接安装

按照目前公开文档，我没有看到单独的人工提交流程，所以更像是“公开 GitHub 仓库 + 被安装和传播”这一套分发方式。
