<!--
CLAUDE.md SEED TEMPLATE — a portable starting point for any new project.

  UNIVERSAL   — copy verbatim on day one; true for any codebase.
  «BRACKETED» — fill in AFTER initial implementation, from the real code.

Everything above the divider is generic.
The trailing section is OPTIONAL, for domain- or workspace-specific rules —
delete it for a standalone, plain project.

Keep the file short: it holds invariants + discipline.
Depth belongs in docs/ (and a code graph if you have one).
Uses semantic line breaks — one clause per line; write the project's docs so too.
Remove this comment after filling in the content.
-->

# «Project» — «one-line what-it-is»

«2–3 sentences: what it does, the stack,
and the ONE doc to read before changing behavior.

## Commands

```sh
«run»            # dev/run
«lint»           # lint gate — must be clean before every commit
«test»           # full suite
«test-one»       # single test file
```

## Commit & release rules   ← UNIVERSAL

- **Commit incrementally and atomically** —
  one cohesive change per commit, never bundle unrelated changes or defer commits into one late batch.
- **Every commit green**: lint + tests clean before each commit, not just at session end.
- **Conventional Commits** (`feat:`, `fix:`, `test:`, `docs:`, `chore:` …).
- Keep `README.md` / `docs/` in step with behavior changes in the same series.
- **`CHANGELOG.md` is curated, not per-commit**:
  user-observable deltas only, grouped by version, curated at bump time.
- **Version bumps** (pre-1.0 `0.x`, breaking → minor):
  propose after a major change or once small ones pile up; never bump silently mid-feature.

## Code standards   ← UNIVERSAL

- Max ~300 lines per file; split at natural boundaries. Modularity over bloat.
- Comments only for non-obvious constraints;
  side-effectful effects get a one-line `// why:` (trigger + observable result).
- **Semantic linebreaks** in Markdown/docs: one clause per line.
- Tests: behavior over implementation detail;
  extract pure logic so it's testable without the framework.

## Working with subagents & tools   ← UNIVERSAL

- Offload research and large implementations to subagents rather than crowding one session:
  a **Sonnet** subagent for scoped research or mechanical work,
  an **Opus** subagent for design-heavy or cross-cutting implementation.
  Hand each the full spec + the relevant `docs/` pointer.
- For "where does X live" questions, prefer a code-graph tool over growing Architecture below.
- Large mechanical refactors go through a codemod
  (jscodeshift / ts-morph / `gofmt -r`), not hand edits —
  write it, run it, review the diff.

## Architecture   ← «FILL AFTER INITIAL IMPLEMENTATION»

«Layers inner → outer, dependency direction stated.
One line per layer: directory, job, key file to read.
A map, not a manual — depth lives in docs/.»

## Invariants (do not "simplify" away)   ← «FILL AS DECISIONS LAND»

«Rules a well-meaning refactor would break.
Each with a one-line why + a `docs/` pointer where relevant.»

## Extended docs   ← UNIVERSAL convention

- Decisions, rationale, and major turning points live in `docs/`, not inline; this file points.
- **One fact, one home**: each topic owned by exactly one doc;
  narrative docs (history, status, plans) link into it, never restate it.
- **Delete plan docs once shipped** — don't leave a stale third copy.
