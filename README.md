<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://readme-typing-svg.demolab.com?font=Inter&weight=500&size=32&duration=2000&pause=1600&color=FFFFFF&center=true&vCenter=true&width=640&lines=Clarify" />
  <img src="https://readme-typing-svg.demolab.com?font=Inter&weight=500&size=32&duration=2000&pause=1600&color=1A1A1A&center=true&vCenter=true&width=640&lines=Clarify" />
</picture>

<p align="center">
  <em>Lightweight intent refinement for AI coding agents.</em>
</p>

<p align="center">
  <a href="https://agentskills.io"><img src="https://img.shields.io/badge/agentskills-SKILL.md-6e45d5?style=flat-square" /></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" /></a>
  <img src="https://img.shields.io/badge/trigger-auto-22c55e?style=flat-square" />
</p>

---

A thin lens between your message and the agent's next action.

Most AI agents rush to act, burning context and tokens on misunderstood requests. **Clarify** pauses just long enough to detect ambiguity — and asks at most **one question** before the agent touches any code.

```
CLEAR REQUEST?  →  Act immediately. No ceremony.
AMBIGUOUS?      →  Ask exactly one question. Then wait.
```

---

## How it works

Clarify scans each incoming message for seven signals of ambiguity:

| Signal | Example |
|--------|---------|
| **Unstated scope** | "add auth" — which method? which routes? |
| **Missing constraints** | "make it faster" — by how much? at what cost? |
| **Vague criteria** | "make it better" — measured how? |
| **Assumed context** | references to files not yet established |
| **Multiple readings** | "refactor the auth" — extract? rename? restructure? |
| **Unstated trade-offs** | "use a database" — which one? why? |
| **Emotional requests** | "this feels messy" — what specifically? |

If the request is clear, the agent proceeds immediately — Clarify adds **zero overhead**.

---

## Quick install

```bash
# Via add-skill (recommended)
npx add-skill ccjh11/clarify
```

Or manually:

```bash
cp SKILL.md ~/.reasonix/skills/clarify/SKILL.md
```

Compatible with **Claude Code** · **Codex CLI** · **Cursor** · **Reasonix** and any agent that follows the [Agent Skills spec](https://agentskills.io).

---

## Design philosophy

Clarify is not a workflow. It's not brainstorming, not planning, not a design phase. Those have their place — Clarify operates *before* any of them.

- **One question max.** Multi-step interviews belong in brainstorming. If more than one thing is ambiguous, pick the most consequential and ask that.
- **Skip freely.** Follow-ups, test commands, typo fixes — don't overthink.
- **A lens, not a gate.** It sharpens intent. It does not block.

---

## License

MIT · [ccjh11](https://github.com/ccjh11)
