---
name: red-team
description: Red-team artifacts using two subagents in parallel and fix what they find. Use when the user says "red-team", "attack this", or wants an adversarial review of a plan, doc, design, or code.
---

# Red Team

Dispatch two subagents **in parallel** (both in a single message) to red-team the artifacts the user
specifies. If no artifacts are specified, ask which to red-team.

Give each subagent a distinct angle:

- **Agent 1 — break it:** failure modes, edge cases, where it falls apart under pressure.
- **Agent 2 — what's missing:** unstated assumptions, gaps, things not considered.

Merge and dedup their findings, then fix the issues the red team surfaced. For anything hard to
reverse, or any not-yet-decided tradeoff, discuss with the user before changing the artifact.
