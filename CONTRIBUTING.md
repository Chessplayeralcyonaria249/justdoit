# Contributing

## Before You Open a PR

- Keep changes scoped.
- Update both `README.md` and `README.ru.md` when messaging changes.
- Update `CHANGELOG.md` under `[Unreleased]`.
- If skill behavior changed, update the skill-level READMEs too.

## Repo Conventions

- Skill source lives in `skills/<name>/`.
- Add assets under `assets/`.
- Keep examples copy-pasteable.
- Prefer product-level language in root docs and operational language in `SKILL.md`.

## Release Notes

- New skill or new top-level component: MINOR bump
- Existing skill updates: PATCH bump
- Docs-only fixes: PATCH bump
