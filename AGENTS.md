# AGENTS.md

Public skill pack for [skills.sh](https://skills.sh/). Each skill is a folder under `skills/` with a `SKILL.md`.

## Layout

- New skills go under `skills/<name>/SKILL.md`.
- `skills/interface-feel-polish/SKILL.md` is the skill body.
- `skills/interface-feel-polish/references/interface-details.md` holds the heuristics. Read only the sections the task needs.
- `skills/interface-feel-polish/README.md` is the per-skill readme.

## Run

```bash
npx skills add https://github.com/Popwers/skills --skill interface-feel-polish
```

## Invariants

- `interface-feel-polish` polishes typography, geometry, motion, and surfaces. It does not redesign the page.
- Heuristics come from Jakub Antolak's article "Details that Make Interfaces Feel Better", written up in `references/interface-details.md`.
- Audits report findings in priority order. Implementations name which heuristics were applied.
