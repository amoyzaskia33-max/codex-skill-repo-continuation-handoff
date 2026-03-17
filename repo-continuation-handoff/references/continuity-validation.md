# Continuity Validation Pattern

Use this after substantial continuity edits when you want stronger confidence than a manual read-through.

## Validation Layers

### 1. Fast local validation

Check the saved continuation anchor for structural drift:

- required sections still exist
- next-step guidance is still explicit
- prompt fields are still present
- "no active task" language still points the next agent toward defining a narrow scope before coding

This can be:

- a small repo-local checker script
- a unit test around representative `AGENTS.md` fixtures
- or both

The exact tooling is repo-specific. The pattern is what matters.

### 2. Blind fresh-agent resume test

Ask a fresh agent that does not inherit the prior chat history to resume from saved repo files only.

Have it answer:

1. What is the main goal?
2. What is the current session scope?
3. What was completed most recently?
4. What is the immediate next step?
5. What must not regress?
6. What requires approval before changing?

If the fresh agent hesitates, answers ambiguously, or needs the old chat to proceed, continuity is still weak.

### 3. Close the loop

If validation exposes ambiguity:

- repair `AGENTS.md`
- update `Session Log`
- clarify the latest milestone or verification status
- rerun the validation

## Rule of Thumb

- Manual read-through is enough for tiny wording edits.
- Use a checker plus a fresh-agent test for meaningful continuity changes, new handoff formats, or repos that often drift across sessions.
