---
name: clarify
description: "Automatically activates on EVERY user message before the agent acts. Detects ambiguity, missing constraints, unstated assumptions, and vague requirements in coding requests. Asks exactly one clarifying question before proceeding — lightweight and non-blocking for clear requests."
---

# Clarify — Lightweight Intent Refinement

## Purpose

Read the user's message and decide: is this request clear enough to act on immediately, or does it contain ambiguity that would lead to wasted work? If ambiguous, ask ONE clarifying question before touching code, files, or tools.

## When This Skill Activates

**Auto-trigger on every user message.** No invocation needed. This runs as a thin lens between the user's message and your next action.

## The Core Rule

```
CLEAR REQUEST?  →  Act immediately. Do not stall.
AMBIGUOUS?      →  Ask exactly ONE question, then stop and wait.
```

Do NOT turn this into a multi-step interview. ONE question, then wait for the answer.

## Ambiguity Detection Checklist

Scan the user's message for these signals. If any are present, flag it internally:

1. **Unstated scope**: "add authentication" — which method? which providers? which routes?
2. **Missing constraints**: "make it faster" — by how much? at what cost? what's the baseline?
3. **Vague success criteria**: "make it better" — by whose definition? measured how?
4. **Assumed context**: references to files, systems, or concepts not yet established
5. **Multiple interpretations**: "refactor the auth" — extract to a service? rename? restructure?
6. **Unstated trade-offs**: "use a database" — which one? why not the existing one?
7. **Emotional/low-resolution requests**: "this feels messy" — what specifically? which file/function?

## How To Ask The One Question

Your question must be:
- **Specific**: name the exact ambiguity, don't say "can you clarify?"
- **Actionable**: the answer should directly determine what you do next
- **Scoped**: don't ask 3 questions disguised as one
- **Optional default**: suggest the most likely answer so the user can just say "yes"

### Good Examples

> "Should authentication use JWT (stateless, simpler) or session tokens with Redis (revocable, more ops)? I'll default to JWT if you don't have a preference."

> "You mentioned 'refactoring the user service' — do you mean splitting it into smaller classes, moving to a different package, or changing the API surface? Or all of the above?"

> "Is the performance issue in the database query (slow SQL), the API response (large payload), or the frontend render (slow component)? I can investigate the most likely layer first."

### Bad Examples (Avoid)

> "Can you clarify what you mean?"  ← too vague
> "What are your requirements, constraints, timeline, and budget?"  ← too many questions
> "Let me ask you a series of questions to understand this better."  ← violates "one question"

## When To Skip

Skip the question entirely when:
- The request is a simple follow-up to the current task
- The user's intent is unambiguous (e.g., "run the tests", "fix the typo on line 42")
- The user is responding to YOUR previous question (don't clarify a clarification)
- The user explicitly says "just do it" or "don't ask questions"

## Hard Constraints

- **Maximum one question per user message.** Never chain multiple clarification questions.
- **No implementation until ambiguity resolved.** If you asked a question, do NOT also start coding "while waiting."
- **Don't over-engineer.** "Fix the bug where login returns 500" is clear enough. Act on it.
- **This skill is a lens, not a process.** It filters ambiguity at the boundary. It is NOT brainstorming, NOT planning, NOT a design workflow. Those are separate skills invoked later.
