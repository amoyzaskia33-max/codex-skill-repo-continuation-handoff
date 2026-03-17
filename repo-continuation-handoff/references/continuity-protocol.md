# Continuity Protocol

Use this protocol when the repo may be touched by multiple agents across multiple sessions, IDE work, or CLI work.

## Goal

Keep continuity stable so the next agent does not need the full transcript to answer:

- what are we trying to achieve
- what are we doing in this session
- how far have we progressed
- what is next
- what must not regress

## Shared Truth

When many tools are involved, use these sources in order:

1. saved repo files
2. repo-root `AGENTS.md`
3. active plan documents referenced from `AGENTS.md`
4. fresh verification output

Do not rely on unsaved IDE buffers or old chat context as the primary truth.

## Start of Session Protocol

Before coding:

1. read `AGENTS.md`
2. identify main goal
3. identify current session scope
4. identify last completed work
5. identify next step
6. identify locked behavior and approval boundaries
7. restate the scope before substantial work

If any of these are unclear, fix the anchor first.

## Mid-Session Checkpoint Protocol

After any meaningful milestone:

1. update `Last Completed Work`
2. update `Current Progress Status`
3. update `Continue From Here`
4. update verification notes if relevant
5. keep the session log concise

Do this when:

- a feature slice is completed
- a bug root cause is found
- a test milestone is reached
- scope changes with user approval

Use this checkpoint decision rule:

- if the goal, scope, plan, and next step are still materially the same, a `Session Log` update is often enough
- if progress state, next step, verification state, or scope materially changes, update the anchor fields and not only the log

## End of Session Protocol

Before stopping:

1. update the continuation anchor
2. record current progress honestly
3. record remaining work
4. record the immediate next step
5. record verification status
6. leave the repo ready for the next agent

## Stability Rules

- Keep one continuity style across sessions.
- Do not reformat the entire anchor unless it improves clarity materially.
- Prefer short operational bullets over narrative summaries.
- Keep `main goal` durable.
- Keep `current session scope` narrow.
- Keep `session log` short and recent.
- Keep `Session Log` as a checkpoint trail, not as a substitute for stale anchor fields.

## Good Outcome

The second, third, or fourth agent should all be able to:

1. open the repo
2. read `AGENTS.md`
3. identify the goal and current scope
4. continue safely

If that is not true, continuity is still weak.
