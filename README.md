# Handoff Skill

Compact the current agent conversation into a handoff document so a fresh session can continue the work with the right context.

[中文 README](README.zh-CN.md)

Use this when a Codex or Claude Code session needs to preserve goal, constraints,
changed files, verification state, open questions, and next actions for another
LLM agent.

`handoff-skill` is a small standalone project that keeps the skill protocol in [SKILL.md](SKILL.md), with ready-to-reference entrypoints for both Codex and Claude Code.

## Skill Integration

- Codex: `.codex/skills/handoff/SKILL.md`
- Claude Code: `.claude/skills/handoff/SKILL.md`
- Root source: `SKILL.md`

The skill is used when an agent needs to write a concise handoff for another agent or a fresh session.

Inspired by ykdojo's handoff skill in [claude-code-tips](https://github.com/ykdojo/claude-code-tips/blob/main/skills/handoff/SKILL.md).

## License

MIT. See [LICENSE](LICENSE).
