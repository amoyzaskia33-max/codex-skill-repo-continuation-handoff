---
name: repo-continuation-handoff
description: Use when finishing substantial repo work or preparing a project for another Codex agent so future sessions can immediately understand what the repo is, what has been completed, and what should be continued next.
---

# Repo Continuation Handoff

## Overview

Leave the repository in a state where a future Codex agent can continue with minimal chat history and without silently regressing existing features. The repo itself should explain the current system state, the latest plans, the next sensible steps, what was completed most recently, and what must not change without approval.

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
   - which plan is currently active
   - what was completed most recently
   - what should be continued next
   - current implemented state
   - locked features that must not regress
   - things that must not change without approval
   - important constraints
   - verification commands
   - operator loop if relevant
   - a copy-paste prompt for future sessions
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
## Current Active Plan
## Last Completed Work
## Continue From Here
## Historical Context
## Current System State
## Locked Features / Non-Regression
## Do Not Change Without Approval
## Important Constraints
## Verification Commands
## Local Operator Loop
## Latest Implementation Landmarks
## Best Next Steps
## Prompt for Future Sessions
## Working Style
```

Keep it concise. Prefer operational facts over long narrative.

## Good Handoff Content

Good:
- exact file paths for plans
- one clearly named active plan
- a short "last completed work" section
- a short "continue from here" section
- current verification commands that actually pass
- real constraints like "still file-backed JSON" or "still unofficial Baileys"
- explicit non-regression features
- specific next steps in priority order

Bad:
- vague phrases like "project mostly done"
- file-by-file changelog dumps
- duplicating the entire conversation
- pretending the repo is clean when it is not
- leaving the next agent to infer which features are safe to touch

## Common Mistakes

- Writing a long summary in chat but not storing it in the repo
- Updating `README.md` but forgetting a dedicated `AGENTS.md`
- Leaving multiple candidate plans without saying which one is current
- Treating old worktrees as still active after merge
- Cleaning status by committing unrelated files
- Forgetting to record how to run or verify the current system
- Forgetting to name the currently active plan
- Forgetting to record the last completed milestone
- Forgetting to state which features must not disappear

## Required Continuation Guardrail

When this skill is used, the next agent should be able to open `AGENTS.md` and answer these questions before coding:
- What is the active plan?
- What was the last completed work?
- What is the immediate next continuation target?
- Which existing features are locked and must not regress?
- Which changes require explicit approval before scope changes?

If those answers are not obvious from the repo handoff, the handoff is incomplete.

## Default Rule

If a user wants future continuation to be easy, the next agent should be able to open the repo, read `AGENTS.md`, identify the active plan and locked features, then continue without needing the full chat transcript.
