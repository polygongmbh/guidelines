## Shell Commands

- Prefer Bash commands whose leading token is auto-allowed (e.g. `grep`, `find`, `git`, `npx vitest`, `npx tsc`) over complex scripts that require extra permission prompts.
- Use the `Write` tool instead of `cat > /tmp/script << 'EOF'` heredocs — heredocs trigger a shell-parser bug ("Unhandled node type: string") that bypasses the allowlist.
- For cross-cutting symbol renames across many files, use `jscodeshift` with an inline transform rather than `sed -i` or ad-hoc Python scripts; it handles AST-level renames safely and avoids regex edge cases.

  ```sh
  npx jscodeshift -t <transform-file-or-inline> src/**/*.{ts,tsx}
  ```

## Workflow

- Before any larger change (major feature, cross-view UI change, broad refactor, or release prep), run `git pull --rebase --autostash` and warn if there are multiple unrelated changed files.
- Use Conventional Commits: `feat:`, `fix:`, `enhance:`, `refactor:`, `test:`, `docs:`, `chore:`
- After each self-contained change, commit — for multi-step tasks **and especially big refactors**, commit incrementally at each natural checkpoint (e.g. "store field added", "consumers switched", "Index unwound", "tests updated") rather than batching everything into a single end-of-task commit
- Prefer `git commit -m "..." <explicit file list>` over `git add ...` + `git commit`
- After finishing work, concisely report added/removed line counts split into production code, test code, and other changes (e.g. documentation or build files).
- Amend the immediately previous local commit when the change is a direct fixup of it; use a new commit otherwise.

When the user says `squash`, inspect recent unpushed commits and suggest sensible squashes for fixups or tightly related follow-ups; list candidates with original and target messages before executing anything.

### Changelog
- Keep `CHANGELOG.md` updated; add user-visible changes to `## [Unreleased]` as you go
- Use `### Added` for new capabilities, `### Changed` for enhancements and changes, `### Fixed` for regressions; omit subheadings when fewer than 4 bullets in a version
- Do not add entries for minor/internal-only changes

### Logging and Toasts
- Use `console.warn`/`console.error` for actionable issues
- New user-facing features must include debug logs enabled by default in dev builds
- Use toasts for significant user-facing outcomes; avoid duplicate/spammy toasts for the same event

## Code Standards & Refactor Policy
- Max 300 lines per file — split at natural boundaries if exceeded
- One component per file; index files export only, no logic
- Before making substantial changes to a file, clean it up appropriately
- Never replicate patterns from legacy files without flagging them
- Do NOT touch files outside the current task scope
