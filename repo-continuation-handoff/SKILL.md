---
name: repo-continuation-handoff
description: Use when finishing substantial repo work or preparing a project for another Codex agent so future sessions can immediately understand what the repo is, what has been completed, and what should be continued next.
---

# Repo Continuation Handoff

## Overview

Leave the repository in a state where a future Codex agent can continue with minimal chat history. The repo itself should explain the current system state, the latest plans, the next sensible steps, and how to verify the setup.

## When to Use

Use this skill when:
- a user says to "rapikan dulu", "biar agent lain bisa lanjut", "siapkan handoff", or similar
- a substantial feature has just been finished and continuity matters
- a repo has scattered plans, worktrees, or implicit context that should be consolidated
- you want the next session to succeed even without the full conversation history

Do not use this for tiny one-off edits that do not change repo understanding.

## Workflow

1. Gather the current repo truth.
   Check:
   - current branch and git status
   - latest relevant commits
   - latest design/plan documents
   - current verification status (`npm test`, build, or equivalent)
   - any remaining constraints or known gaps

2. Consolidate to the repo that should be considered primary.
   - Prefer one clear source repo/branch.
   - If feature work was done in a worktree and is already merged, remove stale worktree references from the handoff.
   - Never hide unresolved branches or dirty state; surface them clearly.

3. Create or update a repo-root `AGENTS.md`.
   Include only high-signal context:
   - what the project is
   - where the source of truth lives
   - which docs should be read first
   - current implemented state
   - important constraints
   - verification commands
   - operator loop if relevant
   - most natural next steps
   - latest important commits or milestones

4. Add a short pointer in `README.md`.
   Do not duplicate the whole handoff. Add a short "continue here" section that points to:
   - `AGENTS.md`
   - the newest relevant plans

5. Clean repo context where appropriate.
   - If plan files are important historical context and truly belong in the repo, stage and commit them.
   - Do not commit unrelated user files just to make `git status` clean.
   - If untracked files remain intentionally, explain that explicitly.

6. Finish with a continuation-ready summary.
   State plainly:
   - repo is or is not clean
   - where the next agent should start
   - what is implemented
   - what the next likely continuation options are

## Recommended `AGENTS.md` Shape

Use this structure when it fits:

```md
# <Project> Agent Notes

## Start Here
## Read Order
## Historical Context
## Current System State
## Important Constraints
## Verification Commands
## Local Operator Loop
## Latest Implementation Landmarks
## Best Next Steps
## Working Style
```

Keep it concise. Prefer operational facts over long narrative.

## Good Handoff Content

Good:
- exact file paths for plans
- current verification commands that actually pass
- real constraints like "still file-backed JSON" or "still unofficial Baileys"
- specific next steps in priority order

Bad:
- vague phrases like "project mostly done"
- file-by-file changelog dumps
- duplicating the entire conversation
- pretending the repo is clean when it is not

## Common Mistakes

- Writing a long summary in chat but not storing it in the repo
- Updating `README.md` but forgetting a dedicated `AGENTS.md`
- Leaving multiple candidate plans without saying which one is current
- Treating old worktrees as still active after merge
- Cleaning status by committing unrelated files
- Forgetting to record how to run or verify the current system

## Default Rule

If a user wants future continuation to be easy, the next agent should be able to open the repo, read `AGENTS.md`, then continue without needing the full chat transcript.
