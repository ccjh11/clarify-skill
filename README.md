<p align="center">
  <img src="https://img.shields.io/badge/Clarify-Intent_Refinement-6e45d5?style=for-the-badge&logo=robotframework&logoColor=white" />
</p>

<p align="center">
  <sub>A thin lens between your message and the agent's action.</sub>
</p>

<p align="center">
  <a href="https://agentskills.io"><img src="https://img.shields.io/badge/spec-SKILL.md-6e45d5?style=flat-square" /></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" /></a>
  <img src="https://img.shields.io/badge/trigger-auto-22c55e?style=flat-square" />
  <img src="https://img.shields.io/badge/compatibility-Claude%20Code%20%7C%20Codex%20%7C%20Cursor%20%7C%20Reasonix-555?style=flat-square" />
</p>

---

Most AI agents rush to act — burning context and tokens on misunderstood requests.

**Clarify** pauses just long enough to detect ambiguity, then asks **at most one question** before the agent touches any code.

```
CLEAR REQUEST?  →  Act immediately. No ceremony.
AMBIGUOUS?      →  Ask exactly one question. Then wait.
```

---

## 🔍 What it detects

Seven signals of ambiguity — a quick internal scan before every action:

| # | Signal | Trigger Example |
|---|--------|----------------|
| 1 | **Unstated scope** | "add auth" — which method? which routes? |
| 2 | **Missing constraints** | "make it faster" — by how much? at what cost? |
| 3 | **Vague criteria** | "make it better" — by whose standard? |
| 4 | **Assumed context** | references to files not yet established |
| 5 | **Multiple readings** | "refactor the auth" — extract? rename? restructure? |
| 6 | **Unstated trade-offs** | "use a database" — which one? why? |
| 7 | **Emotional requests** | "this feels messy" — where? what specifically? |

No ambiguity detected? **Zero overhead** — the agent proceeds immediately.

---

## 📦 Install

```bash
npx add-skill ccjh11/clarify
```

Works with **Claude Code** · **Codex CLI** · **Cursor** · **Reasonix** and any agent following the [Agent Skills spec](https://agentskills.io).

---

## ✨ Design

Clarify is **not** a workflow. It's not brainstorming, not planning, not a design phase.

- **One question max.** Multi-step interviews belong elsewhere. Pick the most consequential ambiguity.
- **Skip freely.** Follow-ups, test commands, typo fixes — don't overthink.
- **A lens, not a gate.** It sharpens intent. It does not block.

---

License · **MIT**  ·  [ccjh11](https://github.com/ccjh11)
