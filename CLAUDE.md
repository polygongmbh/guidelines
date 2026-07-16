# guidelines — portable CLAUDE.md templates & guideline snippets

This repo is **content, not code**:
reusable CLAUDE.md seeds and language/topic guideline fragments
that get copied into other projects.
There is nothing to build, run, or test —
the deliverable is prose that another agent will read as instructions.
Every change is an edit to a document, judged by whether it reads clearly and stays true across many projects.

## Editing discipline

- **Keep it short.** These files are invariants + discipline, not manuals;
  depth belongs in the downstream project's `docs/`, and templates should say so.
- **Universal vs bracketed.** In templates, mark blocks that copy verbatim as universal
  and blocks that need project-specific filling with `«guillemets»` — never leave a real project's specifics baked into a template.
- **One fact, one home.** A convention lives in exactly one fragment;
  other files link to it rather than restating it.
- **Match the surrounding voice** — imperative, terse, second person where a template addresses the agent.
- Use **Semantic line breaks** (sembr) - break lines at clause and sentence boundaries, one thought per line rather than wrapping at a fixed column

## Commit rules

- Commit incrementally and atomically — one cohesive edit per commit, after each change rather than in one late batch.
- Skip Conventional Commit prefixes here — everything is docs, so a prefix adds no signal; write a plain descriptive subject.
- Keep `README.md` in step with any change to what fragments exist or how they're used.
