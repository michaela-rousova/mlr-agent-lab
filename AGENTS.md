# AGENTS.md — working rules

Rules for any agent working in this repo. Claude Code loads this file through
the `@AGENTS.md` import in `CLAUDE.md` — without it, adding `CLAUDE.md` would
make `AGENTS.md` be ignored entirely. Check with `/context` → Memory files.

## 1. Read before you act

Read `README.md` (goal, how to run things) and `PLAN.md` (where things stand,
what is next) before changing anything.

- Do not re-derive what `PLAN.md` already records.
- If the code contradicts `PLAN.md`, say so instead of quietly picking one as truth.
- Update `PLAN.md` when you finish, in the same change.

## 2. Python goes through uv

| Do | Don't |
|---|---|
| `uv run hello.py` | `python hello.py` |
| `uv run python -m <mod>` | `pip install <pkg>` (global or `--user`) |
| `uv add <pkg>` | `pip install -r requirements.txt` by hand |
| `uv sync` after pulling | editing `.venv/` by hand |

No global `pip install`, ever. If a dependency is needed, it goes in
`pyproject.toml` via `uv add` so the next person gets it from `uv sync`.

**Verified on this machine (2026-10-21), uv 0.13.1:**

- `uv run hello.py` → works, prints `hello`.
- `uv add <pkg>` → **fails**: `No pyproject.toml found`. This repo is not a uv
  project yet. Run `uv init` before using `uv add` (tracked in `PLAN.md`).

## 3. Run checks before you say it is done

"Done" is a claim about behaviour, so demonstrate the behaviour.

- Run the check, then quote the command and its actual output.
- A check you did not run did not pass. Name anything unverified instead of
  letting it read as a success.
- If it fails, report the failure with the output. No hedging, no "should work".
- For the docs in this repo the check is narrow: a documented command must be
  one you actually ran, or one you flagged as untested.
- Before anything outward-facing and hard to undo (pushing to a public repo,
  deleting, sending), show what will happen and confirm first.

## 4. Record the run

Log the run in `RUNS.md`: model, what was asked, how it was checked. Append;
do not rewrite earlier entries.
