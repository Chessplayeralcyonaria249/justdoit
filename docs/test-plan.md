# Test Plan

## Source
- Task: package `justdoit` as a standalone skill repository
- Plan file: `docs/plans.md`
- Status file: `docs/status.md`
- Repo context: documentation-heavy skill repository
- Last updated: 2026-03-13

## Validation Scope
- In scope: repo structure, skill packaging, README clarity, install instructions, asset rendering
- Out of scope: remote GitHub release, live install from the remote before the remote exists

## Environment / Fixtures
- Data fixtures: current local `justdoit` skill source in `~/.codex/skills/justdoit`
- External dependencies: local git, markdown rendering on GitHub, future Codex `skill-installer`
- Setup assumptions: local filesystem access; future repo owner is `serejaris`

## Test Levels

### Unit
- Skill frontmatter and structure validate with `quick_validate.py`

### Integration
- Root README links point to real local files
- Skill README installation instructions match repo layout

### End-to-End / Smoke
- A user can understand what the repo does from the root README alone
- A user can identify how to install the skill in Codex
- The GIF path resolves from the repo markdown

## Negative / Edge Cases
- Missing `README.ru.md` or `README.md`
- Broken local asset path in README
- Drift between root README install instructions and skill README install instructions
- Skill name mismatch between folder, frontmatter, and installer path

## Acceptance Gates
- [ ] `python3 /Users/ris/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/justdoit`
- [ ] `test -f README.md && test -f README.ru.md`
- [ ] `test -f skills/justdoit/README.md && test -f skills/justdoit/README.ru.md`
- [ ] `test -f assets/justdoit.gif`
- [ ] `git status --short`

## Release / Demo Readiness
- [ ] Root README sells the repo clearly
- [ ] Skill README explains install and usage clearly
- [ ] Changelog reflects current work
- [ ] Repo tree is clean and coherent

## Command Matrix
```sh
find . -maxdepth 3 -type f | sort
python3 /Users/ris/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/justdoit
rg -n "justdoit|skill-installer|assets/justdoit.gif" README.md README.ru.md skills/justdoit/README.md skills/justdoit/README.ru.md
git status --short
```

## Open Risks
- Remote install URL cannot be proven end-to-end before the GitHub repo exists
- Third-party GIF hosting may be unstable if the asset is not checked into the repo

## Deferred Coverage
- GitHub Actions
- Release automation
- Live installer verification from the public repo
