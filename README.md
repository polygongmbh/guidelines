# Guidelines

Portable **CLAUDE.md** templates and guideline fragments
for driving [Claude Code](https://claude.com/claude-code) (and similar agents) consistently across projects.

Instead of re-deriving conventions in every repo,
start from a shared seed and layer topic-specific fragments on top.

## Contents

| File | Purpose |
| --- | --- |
| [`claude-md-template.md`](claude-md-template.md) | Seed CLAUDE.md for a brand-new project — universal blocks copy verbatim, `«bracketed»` blocks get filled from real code. |
| [`ts.md`](ts.md) | TypeScript-specific guideline fragment (shell, workflow, changelog, code standards). |
| [`CLAUDE.md`](CLAUDE.md) | Governs work **inside this repo** |

## Using a template

1. Copy `claude-md-template.md` into a new project as `CLAUDE.md`.
2. Copy the **universal** blocks verbatim on day one.
3. Fill the `«bracketed»` blocks *after* the initial implementation, from the real code.
4. Delete the leading HTML comment and any optional trailing section you don't need.
5. Append relevant topic fragments (e.g. the contents of `ts.md`) under matching headings.

## Automatic use

Global Claude Code config consumes this repo without copying it:
`~/.claude/CLAUDE.md` tells the agent to seed every new `CLAUDE.md` (incl. `/init`) from the template,
and a `SessionStart` hook (`~/.claude/hooks/seed-claude-md.sh`) injects the same pointer
whenever a git project has no `CLAUDE.md`.
Both locate the repo via `$PROJECTS/guidelines`,
so the checkout can live at a different path on each device.

## Contributing

- One topic per fragment file (`<topic>.md`); one fact, one home.
- Keep it short — invariants and discipline, not manuals.
