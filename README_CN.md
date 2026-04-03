# Agent Relay Skills

✨ 面向 Codex 风格 agent 的本地模式与 GitHub 模式 relay 技能集合。

`Agent Relay Skills` 是一套把 [yan5xu/code-relay](https://github.com/yan5xu/code-relay) 思路做成可复用 skill 的实现集合。

它的目标不是替代原项目，而是把那篇文章里的核心做法封装成更容易传播和复用的技能包，方便别人直接安装和使用。

[English README](./README.md)

## 包含的技能

### 本地模式

- `agent-relay-local-setup`：初始化或刷新本地 `code relay`
- `agent-relay-local-handoff`：从 `AGENTS.md` 和交接文档恢复上下文
- `agent-relay-local-update`：手动强制刷新 `STATUS / CHECKPOINT / HANDOFF / LEADERBOARD`

### GitHub 模式

- `agent-relay-github-setup`：把 relay 工作流映射到 GitHub Issues / Projects / comments
- `agent-relay-github-handoff`：从 GitHub relay issue 和交接 comment 恢复上下文
- `agent-relay-github-update`：手动刷新 GitHub 上的 relay 状态

## 命名规范

统一采用：

- `agent-relay-local-*`
- `agent-relay-github-*`

其中：

- `setup`：负责搭结构
- `handoff`：负责读取和恢复
- `update`：负责手动刷新

## 推荐用法

### 本地仓库

1. 使用 `$agent-relay-local-setup`
2. 使用 `$agent-relay-local-handoff` 恢复上下文
3. 使用 `$agent-relay-local-update` 手动刷新 relay 状态

### GitHub 模式仓库

1. 使用 `$agent-relay-github-setup`
2. 使用 `$agent-relay-github-handoff` 恢复 issue / comment 中的 relay 状态
3. 使用 `$agent-relay-github-update` 手动刷新 GitHub relay 状态

## 和原始文章的关系

这个仓库是对 [yan5xu/code-relay](https://github.com/yan5xu/code-relay) 的封装和实现扩展，重点在于：

- 本地模式
- GitHub 模式
- 统一命名
- setup / handoff / update 职责拆分
- 更适合在不同仓库之间传播和复用
