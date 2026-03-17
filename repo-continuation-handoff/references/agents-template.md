# AGENTS.md Continuation Template

Use this as the default continuation anchor. Keep it short, factual, and easy to scan.

```md
# <Project> Agent Notes

## Start Here
- Read this file first.
- Read the active plan next: `<path-to-plan>`
- Verify current repo state before coding.

## Main Goal
- <durable project goal>

## Current Session Scope
- <narrow scope for the next session only>

## Active Plan
- Source of truth: `<path>`
- Current phase: `<phase or milestone>`

## Last Completed Work
- <latest finished milestone>
- <important files touched>
- <what was verified>

## Current Progress Status
- Overall progress: <not started | in progress | mostly done | blocked | ready for final verification>
- Current session progress: <short status>

## Continue From Here
- Immediate next step: <single best next task>
- Then: <optional next one or two tasks>

## Current System State
- <what exists today>
- <important architecture or runtime facts>
- <known technical shortcuts that still remain>

## Locked Features / Non-Regression
- <behavior that must keep working>
- <UI or API contracts that must not disappear>

## Do Not Change Without Approval
- <scope expansions>
- <risky refactors>
- <behavioral changes with non-obvious product impact>

## Verification Commands
- `<command>`
- `<command>`

## Open Questions / Known Gaps
- <known issue>
- <missing test>
- <decision still pending>

## Session Log
- <YYYY-MM-DD or session label> - scope: <...>; done: <...>; next: <...>
- Keep latest entries first.
- Keep this concise; do not turn it into a full changelog.

## Prompt for Future Sessions
Main goal: <...>
Current session scope: <...>
Already done: <...>
Do not change: <...>
Definition of done: <...>

Continue only within this scope unless the user expands it.
```

## Writing Rules

- Write one durable `main goal`, not a vague summary.
- Keep `current session scope` narrow and temporary.
- Prefer bullets over paragraphs.
- Record exact file paths for active plans.
- Record only the latest high-signal milestone in `Last Completed Work`.
- Keep `Continue From Here` actionable and ordered.
- Keep `Current Progress Status` current so future agents know whether they are resuming build-out, debugging, or final verification.
- Keep `Session Log` short and recent; enough to anchor continuity across multiple agents.
