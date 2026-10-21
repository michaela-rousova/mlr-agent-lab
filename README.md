# mlr-agent-lab

A small playground for how a coding agent should work in a repo: the working
rules live in [`AGENTS.md`](AGENTS.md), progress in [`PLAN.md`](PLAN.md), and
each agent run is logged in [`RUNS.md`](RUNS.md).

The code itself is deliberately trivial (`hello.py`) — the subject of this lab
is the working rules and the run log, not the Python.

> Sharpen this goal statement when the lab has a concrete target.

## Requirements

- [uv](https://docs.astral.sh/uv/) — checked with uv 0.13.1, Windows
- Python 3.14 present on PATH (uv resolves its own interpreter regardless)

## Run it

```bash
uv run hello.py        # -> hello
```

`uv run python hello.py` works too. There are no dependencies, so this runs
without a lockfile.

`uv add <pkg>` does **not** work yet — it needs a `pyproject.toml`, which this
repo does not have. Run `uv init` first (next step in `PLAN.md`).

## Layout

| Path | What it is |
|---|---|
| `AGENTS.md` | Working rules for agents. Loaded via `CLAUDE.md`. |
| `CLAUDE.md` | One import line pointing at `AGENTS.md`. |
| `PLAN.md` | Where things stand, what is next. |
| `RUNS.md` | Log of agent runs: model, request, check. |
| `hello.py` | `print("hello")` |
| `.claude/settings.local.json` | Local-only permission approvals, gitignored. |

## Layout note

`.claude/settings.local.json` is gitignored on purpose — it holds this
machine's permission approvals and should not be shared.
