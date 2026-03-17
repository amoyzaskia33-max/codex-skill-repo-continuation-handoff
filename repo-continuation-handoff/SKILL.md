---
name: repo-continuation-handoff
description: Use when resuming repo work across sessions or preparing a repo for future continuation. Trigger on requests like "continue this repo", "lanjutkan", "pick up from last session", "buat handoff", or when goals drift between sessions. Establish and maintain one source of truth for the main goal, current scope, completed work, progress status, next step, locked behavior, approval boundaries, and verification so every future agent can continue cleanly without the full chat history.
---

# Repo Continuation and Handoff

## Objective

Make continuation cheap in tokens and stable in focus. A future agent should be able to open the repo, read one anchor document, and continue without reconstructing the whole conversation.

## Core Rules

- Create one authoritative continuation anchor, usually repo-root `AGENTS.md`.
- Separate `main goal` from `current session scope`.
- Batch work by checkpoints; do not optimize for per-keystroke live pairing.
- Prefer one clearly named active plan.
- Record non-regression rules and approval boundaries.
- End substantial sessions with an in-repo handoff, not only a chat summary.
- Treat continuity as a repeating protocol for every session, not a one-time handoff step.
- Preserve useful prior continuity notes; normalize and extend them instead of replacing them with a new style every session.

## Bundled References

- Read `references/agents-template.md` when creating or normalizing repo-root `AGENTS.md`.
- Read `references/session-checklist.md` when resuming a repo, writing a handoff, coordinating with a user working from an IDE or CLI, or deciding whether a checkpoint only needs `Session Log` updates.
- Read `references/continuity-protocol.md` when you need the full cadence for start-of-session, mid-session checkpoint, end-of-session updates, and anchor-maintenance decisions.

## Mandatory Continuity Protocol

When this skill is active, every agent should maintain the same continuity shape:

1. Start the session by reading and trusting the current continuation anchor.
2. Repair missing or stale continuity fields before coding.
3. Keep work inside the declared session scope.
4. Update progress after meaningful milestones, not only at the very end.
5. End the session by leaving the repo in a continuation-ready state again.

Do not treat `AGENTS.md` as archival prose. Treat it as the shared operating note for the next agent.

## Session Cadence

Use this three-phase rhythm for every substantial session:

### Start of session

- Read `AGENTS.md`
- identify the main goal
- identify the current session scope
- identify the last completed work
- identify the next step
- restate the scope before doing substantial work

### During the session

- keep one narrow working scope
- if scope changes, update the anchor intentionally
- if the direction is unchanged, log the checkpoint in `Session Log` and refresh `Last Completed Work` only when it adds real signal
- if scope, next step, progress state, or verification meaningfully changes, update the anchor fields and not only `Session Log`
- after a meaningful milestone, refresh `Last Completed Work`, `Continue From Here`, and verification notes
- if the user works in an IDE or CLI, re-read saved files before continuing

### End of session

- update the continuation anchor
- record what was completed in this session
- record what remains
- record the immediate next step
- record verification status honestly
- leave the next agent with a clear, single starting point

## Resume Workflow

1. Read the continuation anchor before coding.
2. Answer these questions explicitly:
   - What is the main goal?
   - What is the current session scope?
   - What was completed most recently?
   - What is the immediate next step?
   - What must not regress?
   - What requires approval before changing?
3. Repair the anchor first if those answers are not obvious.
4. Restate the active scope in chat before substantial work.
5. Stay inside the current scope unless the user expands it.
6. Re-read saved files when collaborating with a user in an IDE; do not assume live unsaved editor state.
7. Update the anchor after meaningful progress, not only at the end.

## Handoff Workflow

1. Gather repo truth:
   - branch and dirty state
   - active plan docs
   - latest completed milestone
   - verification status
   - known gaps or open questions
2. Consolidate to one source of truth:
   - prefer repo-root `AGENTS.md`
   - point to detailed plans instead of duplicating them
   - mark stale plans or worktrees as inactive or historical
   - if `AGENTS.md` already exists, preserve valid facts and normalize structure instead of rewriting blindly
3. Create or update the continuation anchor with these sections:
   - `Start Here`
   - `Main Goal`
   - `Current Session Scope`
   - `Active Plan`
   - `Last Completed Work`
   - `Continue From Here`
   - `Current System State`
   - `Locked Features / Non-Regression`
   - `Do Not Change Without Approval`
   - `Verification Commands`
   - `Open Questions / Known Gaps`
   - `Prompt for Future Sessions`
4. Add or refresh a short pointer in `README.md`.
5. Finish with a concise chat summary that matches the repo handoff.
6. Make sure the updated repo state would still make sense if a third or fourth agent continued after the next one.
7. Run a consistency check across the anchor:
   - `Current Session Scope`
   - `Continue From Here`
   - `Open Questions / Known Gaps`
   - `Prompt for Future Sessions`
   These fields should describe the same continuation state and should not contradict or duplicate each other.

## Default Continuation Anchor

Use this structure when it fits:

```md
# <Project> Agent Notes

## Start Here
## Main Goal
## Current Session Scope
## Active Plan
## Last Completed Work
## Continue From Here
## Current System State
## Locked Features / Non-Regression
## Do Not Change Without Approval
## Verification Commands
## Open Questions / Known Gaps
## Prompt for Future Sessions
```

Keep sections short and operational.

## Session Prompt Templates

Use this at the start of a new session:

```text
Main goal:
Current session scope:
Already done:
Do not change:
Definition of done:

Continue only within this scope.
```

Use this at the end of a substantial session:

```text
Handoff:
- main goal
- current session scope
- completed this session
- remaining work
- locked features
- changed files
- verification status
- next step
```

## Anchor Maintenance Decision Rule

Use this quick rule during continuation work:

- `Session Log only` when the main goal, current session scope, active plan, non-regression rules, approval boundaries, and immediate next step are still materially the same.
- Update the main anchor sections when any of these change materially:
  - `Main Goal`
  - `Current Session Scope`
  - `Active Plan`
  - `Current Progress Status`
  - `Continue From Here`
  - `Open Questions / Known Gaps`
  - verification status

If the next agent could read the current `Session Log` and still continue safely, a log-only update is usually enough. If the next agent could drift or misread the repo state, update the anchor itself.

## Anti-Drift Guardrails

- Treat `main goal` as durable and `current session scope` as temporary.
- Prefer one goal per session.
- Do not restart from a full repo audit unless asked or the anchor is missing.
- Do not rely on chat-only context for future continuation.
- Use the agent mainly at checkpoints: planning, review, debugging, validation, and handoff.
- If the user is implementing elsewhere, wait for saved files, then re-read them before reviewing or continuing.
- When IDE, CLI, and agent work coexist, treat saved repo files plus `AGENTS.md` as the shared source of truth.
- Keep the continuity format stable across agents so the repo does not accumulate incompatible handoff styles.
- Before ending the session, scan for stale scope lines or duplicated open questions inside the anchor.

## Common Mistakes

- Mixing goal, scope, and next step into one vague paragraph
- Leaving multiple active plans without naming the current one
- Writing only a chat summary and no repo handoff
- Expanding scope during a narrow bugfix session without approval
- Forgetting approval boundaries
- Forgetting to update verification after major changes
- Updating only the final summary while leaving stale progress fields in the anchor
- Rewriting the continuation anchor in a new style every session so later agents must re-parse it from scratch
- Updating `Prompt for Future Sessions` but forgetting to sync `Current Session Scope` or `Continue From Here`
- Leaving duplicate items in `Open Questions / Known Gaps`

## Completion Test

Before considering the handoff complete, make sure a fresh agent can answer:

- What is the main goal?
- What is the scope for the next session?
- What was completed most recently?
- What is the immediate next step?
- What must not regress?
- What requires approval before changing?

If not, keep refining the continuation anchor.
