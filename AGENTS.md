# AGENTS.md

Public skill pack for [skills.sh](https://skills.sh/). Each skill is a folder under `skills/` with a `SKILL.md`.

## Layout

- `skills/interface-feel-polish/SKILL.md` is the skill body.
- `skills/interface-feel-polish/references/interface-details.md` holds the heuristics. Read only the sections the task needs.

## Install

```bash
npx skills add https://github.com/Popwers/skills --skill interface-feel-polish
```

## Constraints

New skills belong under `skills/<name>/`. Do not add an app toolchain or Vite+.
