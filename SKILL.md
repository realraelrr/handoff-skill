---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up.
argument-hint: "What will the next session be used for?"
---

Write a concise handoff document that lets a fresh agent continue the current work without rereading the whole conversation.

Save it under the current project when possible:

- In a git repo, use `.state/handoffs/` under the repo root.
- Outside a git repo, use the system temp directory.
- Use `mktemp` for uniqueness and keep a `.md` extension. Avoid templates like `handoff-XXXXXX.md`; on macOS/BSD, create `handoff-XXXXXX` first, then rename it to add `.md`.

Use `.state/` as agent operational workspace. Do not treat handoff files as product source or commit them by default.

The handoff must include:

- Goal
- Current state, including done, remaining, and only the key files/artifacts needed to continue
- What worked
- What didn't work or remains blocked
- Verification, with exact commands and pass/fail signals
- Next steps, starting with the next concrete action

Keep it concise. Reference existing plans, PRDs, ADRs, issues, commits, diffs, or other artifacts by path or URL instead of duplicating them.

After writing, read the handoff once to verify it is complete enough for a new agent to act from it, then report the saved path.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.
