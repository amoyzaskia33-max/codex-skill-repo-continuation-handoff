# Resume and Handoff Checklist

Use this checklist to reduce drift across sessions and across IDE, CLI, and agent workflows.

## Resume Checklist

Before coding, confirm:

- What is the main goal?
- What is the scope for this session?
- What was completed most recently?
- What is the immediate next step?
- What behavior is locked?
- What changes require approval?

If any answer is missing, repair `AGENTS.md` first.

## Handoff Checklist

Before ending a substantial session, record:

- main goal
- current session scope
- completed this session
- current progress status
- remaining work
- changed files
- verification status
- locked features
- approval boundaries
- immediate next step

Then check that these fields agree with each other:

- `Current Session Scope`
- `Continue From Here`
- `Open Questions / Known Gaps`
- `Prompt for Future Sessions`

Store this in the repo, not only in chat.

## When `Session Log` Is Enough

Use a concise `Session Log` update when:

- the main goal is unchanged
- the current session scope is unchanged
- the active plan is unchanged
- locked behavior is unchanged
- approval boundaries are unchanged
- the immediate next step is still materially the same

Typical examples:

- one small subtask finished inside the same scope
- a bug root cause was found but the plan is unchanged
- one verification command was run successfully
- an IDE-saved file was re-read and continuity did not shift

If needed, refresh `Last Completed Work` too, but do not rewrite the whole anchor just to record a small checkpoint.

## When the Main Anchor Must Be Updated

Update `AGENTS.md` beyond `Session Log` when any of these shift materially:

- `Main Goal`
- `Current Session Scope`
- `Active Plan`
- `Current Progress Status`
- `Continue From Here`
- `Open Questions / Known Gaps`
- verification state
- locked behavior or approval boundaries

Rule of thumb:

- if the next agent could misread the current direction, update the anchor
- if the prompt for the next session should change, update the anchor

## Anti-Drift Rules

- One main goal can span many sessions.
- One session should usually have one narrow scope.
- Do not let a bugfix session silently turn into a refactor session.
- Do not let the newest error overwrite the project goal in your mental model.
- Use the agent at checkpoints, not for every small edit.

## IDE / CLI / Agent Coordination

- Unsaved IDE changes are not visible to the agent.
- Saved files on disk are the shared truth.
- `AGENTS.md` is the continuity truth.
- If the user edits in an IDE, re-read the saved files before reviewing or continuing.
- If multiple tools are used, prefer short checkpoint updates instead of continuous micro-guidance.
- Keep the same continuity shape across sessions so later agents do not need to re-learn the format.
- Remove duplicated open questions and stale scope text before ending the session.

## Good Session Start Prompt

```text
Main goal:
Current session scope:
Already done:
Do not change:
Definition of done:

Continue only within this scope.
```

## Good Session End Prompt

```text
Create a handoff with:
- main goal
- current session scope
- completed this session
- remaining work
- changed files
- verification status
- next step
```
