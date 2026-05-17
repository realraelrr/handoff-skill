# Handoff Skill

**将当前 Agent 对话压缩为交接文档，让新会话带着正确上下文继续工作。**

[English README](README.md)

`handoff-skill` 是一个独立的小型项目，将 skill 协议定义在 [SKILL.md](SKILL.md) 中，并为 Codex 和 Claude Code 各提供就绪可用的入口。

## 它做什么

当 agent 需要将当前对话的工作上下文传递给新会话或另一个 agent 时，触发此 skill。它会生成一份结构化的交接文档，写入项目的 `.state/handoffs/` 目录，包含以下部分：

- 当前状态
- 重要文件/产物
- 已完成的变更
- 验证记录
- 待定决策
- 后续步骤
- 建议的后续 skill

不会重复已有产物（PRD、计划、ADR、issue、commit、diff）中的内容，而是通过路径或 URL 引用它们。

## Skill 集成

- Codex：`.codex/skills/handoff/SKILL.md`
- Claude Code：`.claude/skills/handoff/SKILL.md`
- 根目录源文件：`SKILL.md`

三份文件内容完全一致，根目录 `SKILL.md` 是唯一 source of truth。

如果用户在触发时传入了参数，skill 会将其视为下一次会话的工作方向描述，并据此调整交接文档的内容。

## 设计原则

- **最小化**：纯 skill 定义，无运行时依赖，无构建步骤
- **双平台**：同时支持 Claude Code 和 Codex
- **项目本地**：交接文件写入项目 `.state/handoffs/`，不提交到版本控制
- **可复用**：任何 agent 或新会话都可以读取交接文档并继续工作

灵感来自 ykdojo 的 [claude-code-tips](https://github.com/ykdojo/claude-code-tips/blob/main/skills/handoff/SKILL.md) 中的 handoff skill。

## License

MIT. See [LICENSE](LICENSE).
