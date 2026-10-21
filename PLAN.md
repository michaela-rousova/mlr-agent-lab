# PLAN.md

Read me before changing anything (rule 1 of `AGENTS.md`). Update me when you
finish.

## Where things stand

Scaffolding exists; nothing has been built yet. The repo is a public GitHub
project with one script and the working-rule docs.

## Done

- 2026-10-21 — Repo published: <https://github.com/michaela-rousova/mlr-agent-lab>,
  public, branch `main`.
- 2026-10-21 — Working rules written to `AGENTS.md`, pulled in by `CLAUDE.md`.
  `README.md`, `PLAN.md`, `RUNS.md` created.
- 2026-10-21 — `.claude/settings.local.json` gitignored so local permission
  approvals stay off the public repo.
- 2026-10-21 — Docs committed and pushed as `de910b1`. Remote `main` verified
  to carry all five files.

## Known-broken

- **`uv add` fails.** No `pyproject.toml` exists, so uv has no project to add
  to: `error: No pyproject.toml found in current directory or any parent
  directory`. Rule 2 of `AGENTS.md` therefore cannot be followed as written
  until this is fixed.

## Next step

1. `uv init` to make this a real uv project, which unblocks `uv add`.
   Decide first: application or library, and which Python version.
   `uv init` also drops in its own `main.py` and may touch `README.md` — keep
   an eye on it.
2. Re-run the checks in `AGENTS.md` rule 2 and drop the "Known-broken" entry.
3. Give `README.md` a real goal statement.

## Open questions

- What is the lab actually testing — the agent rules themselves, or a model's
  ability to follow them? The answer shapes `RUNS.md`.
- Should `RUNS.md` entries be written by the agent, or filled in by you after
  reviewing a run?
