# Codex Skill: Repo Continuation Handoff

Public repository for the Codex skill `repo-continuation-handoff`.

This skill helps an agent leave a repository in a continuation-ready state so future Codex sessions can resume quickly without depending on long chat history.

## What The Skill Does

The skill guides an agent to:
- gather the real current repo state
- consolidate the primary repo or branch
- create or update a repo-level `AGENTS.md`
- add a short continuation pointer in `README.md`
- preserve only high-signal context for the next agent

The result is a repo that answers:
- what this project is
- what has already been implemented
- what constraints still matter
- what should be continued next

## Skill Layout

```text
repo-continuation-handoff/
  SKILL.md
  agents/
    openai.yaml
```

## Install

### Option 1: Manual copy

Clone this repository, then copy the skill folder into your local Codex skills directory.

Windows PowerShell:

```powershell
git clone https://github.com/amoyzaskia33-max/codex-skill-repo-continuation-handoff.git
Copy-Item -Recurse -Force .\codex-skill-repo-continuation-handoff\repo-continuation-handoff $HOME\.codex\skills\
```

macOS / Linux:

```bash
git clone https://github.com/amoyzaskia33-max/codex-skill-repo-continuation-handoff.git
cp -R ./codex-skill-repo-continuation-handoff/repo-continuation-handoff ~/.codex/skills/
```

### Option 2: Direct use as reference

You can also read the skill directly from this repository and copy its contents into your own skill library if you prefer.

## When To Use

Use this skill when:
- finishing substantial repo work
- preparing a repo for another Codex agent
- cleaning up context before stopping
- making sure future continuation does not depend on the full chat transcript

## Typical Result In A Repo

When the skill is used well, the target repo usually ends up with:
- a repo-root `AGENTS.md`
- a short continuation pointer in `README.md`
- clear references to the latest relevant plans
- explicit next steps and verification commands

## Example Prompt

```text
Use $repo-continuation-handoff to prepare this repo so future agents can continue instantly.
```

## License

MIT
