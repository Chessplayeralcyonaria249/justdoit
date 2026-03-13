# justdoit Skill

A Codex skill that turns a vague task into a clear execution pack, then asks before starting execution.

## Problem

Most long Codex runs fail before implementation, not during it:
- the repo is not scanned properly
- the plan lives only in chat
- execution starts before validation is defined
- the user gets a wall of prompt text instead of a clear "here is what happens next"

## Solution

`justdoit` makes Codex behave like an execution operator:
- inspect the repo first
- create `plans.md`, `status.md`, and `test-plan.md`
- summarize the proposed run in plain language
- ask for confirmation before execution
- continue with an execution loop only after approval

## Installation

In Codex, ask:

```text
Use $skill-installer to install https://github.com/serejaris/justdoit/tree/main/skills/justdoit
```

That is enough for another Codex agent to self-install the skill from the repo.

Manual install:

```bash
cp -R skills/justdoit ~/.codex/skills/
```

Restart Codex after installation.

## When To Use It

- "turn this task into a plan pack"
- "prepare plans.md / status.md for this repo"
- "break this PRD into milestones"
- "before you start, analyze the repo and propose execution"

## What You Get

- `plans.md` as the source of truth
- `status.md` as the live run log
- `test-plan.md` as the validation gate
- a short user-facing execution proposal instead of a prompt dump

## Key Behavior

- repo-aware planning
- dependency-safe milestones
- validation-first execution
- product-level communication
- explicit confirmation before execution
