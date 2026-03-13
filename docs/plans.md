# Plans

## Source
- Task: Launch `justdoit` as a standalone release-ready Codex skill repository
- Canonical input: user request in Codex chat on 2026-03-13
- Repo context: new standalone repository modeled after `ris-claude-code`
- Last updated: 2026-03-13

## Assumptions
- The repository name is `justdoit`.
- Initial scope is one installable skill, not a multi-skill collection.
- Release packaging is local-only for now; no remote push in this run.

## Validation Assumptions
- Structural validation is based on file presence, skill validation, and markdown readability checks.
- Remote install flow is documented using the intended future GitHub path `serejaris/justdoit`.

## Milestone Order
| ID | Title | Depends on | Status |
| --- | --- | --- | --- |
| M1 | Create repo structure and execution docs | - | [x] |
| M2 | Package the `justdoit` skill inside the repo | M1 | [x] |
| M3 | Ship bilingual README and install docs | M2 | [x] |
| M4 | Add branded visual and polish release assets | M3 | [x] |
| M5 | Validate repo shape and prepare release handoff | M4 | [x] |

## M1. Create repo structure and execution docs `[x]`
### Goal
- New repo exists with the folders and files needed to work like a real skill repository.

### Tasks
- [x] Create local git repo and base folders
- [x] Add `docs/plans.md`, `docs/status.md`, `docs/test-plan.md`
- [x] Add repo-level governance files

### Definition of Done
- The repo can be opened and understood without extra chat context.
- Execution docs exist and point to the next unfinished milestone.

### Validation
```sh
find . -maxdepth 2 -type d | sort
find docs -maxdepth 1 -type f | sort
```

### Known Risks
- Repo structure may still need adjustment once install/readme flow is in place.

### Stop-and-Fix Rule
- If required top-level files are missing, add them before moving on.

## M2. Package the `justdoit` skill inside the repo `[x]`
### Goal
- The repo contains a self-contained skill folder with the latest `justdoit` instructions and references.

### Tasks
- [x] Copy `SKILL.md`
- [x] Copy reference templates
- [x] Add skill-level README files
- [x] Verify skill wording matches repository positioning

### Definition of Done
- `skills/justdoit/` is installable and documented.

### Validation
```sh
find skills/justdoit -maxdepth 2 -type f | sort
python3 /Users/ris/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/justdoit
```

### Known Risks
- Root positioning and skill wording may drift if they are edited separately.

### Stop-and-Fix Rule
- If the skill fails validation or references are missing, fix that before README work continues.

## M3. Ship bilingual README and install docs `[x]`
### Goal
- A human understands what `justdoit` is, why it exists, and how to install it in Codex.

### Tasks
- [x] Write root `README.md`
- [x] Write root `README.ru.md`
- [x] Write `skills/justdoit/README.md`
- [x] Write `skills/justdoit/README.ru.md`
- [x] Verify install instructions are clear and consistent

### Definition of Done
- Both languages explain the product clearly.
- Codex install path is obvious to a user and an agent.

### Validation
```sh
test -f README.md && test -f README.ru.md
test -f skills/justdoit/README.md && test -f skills/justdoit/README.ru.md
```

### Known Risks
- Product messaging may slip into technical jargon.

### Stop-and-Fix Rule
- If the README reads like internal notes instead of a product page, rewrite before continuing.

## M4. Add branded visual and polish release assets `[x]`
### Goal
- The repo feels intentional and memorable, not like a bare skill dump.

### Tasks
- [x] Add Shia LaBeouf "Just Do It" GIF asset
- [x] Verify README rendering with image
- [x] Review asset naming and path stability

### Definition of Done
- README renders the GIF correctly from the repo.

### Validation
```sh
test -f assets/justdoit.gif
rg -n "assets/justdoit.gif" README.md README.ru.md
```

### Known Risks
- Third-party GIF source may become unavailable or unstable.

### Stop-and-Fix Rule
- If the GIF source or file is broken, replace it before release prep.

## M5. Validate repo shape and prepare release handoff `[x]`
### Goal
- The repository is ready for review, commit, and later release.

### Tasks
- [x] Run structural checks
- [x] Review git status
- [x] Summarize remaining release actions

### Definition of Done
- Repo is internally consistent and easy to release.

### Validation
```sh
find . -maxdepth 3 -type f | sort
git status --short
```

### Known Risks
- The future remote repo may require README/install wording tweaks.

### Stop-and-Fix Rule
- If required repo files are still missing, do not call the repo release-ready.
