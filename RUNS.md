# RUNS.md

Log of agent runs in this lab. Newest last. Append; do not rewrite earlier
entries.

Each entry records three things: the **model** as `/status` reports it, what
was **asked**, and how the result was **checked**.

## Model in use

| Field | Value |
|---|---|
| Model | `agentic` |
| Claude Code | 2.1.299 |
| Aliases | opus → `thinker`, sonnet → `agentic`, haiku → `mini` |

`agentic` is an alias on a custom API gateway, not a public Claude model id —
the client cannot see which model sits behind it. Per the Claude Code docs,
`/status` reports the alias you supplied rather than the resolved model, so the
Model line should read `agentic`. Read here from `ANTHROPIC_MODEL` and
`claude --version`, **not** from `/status` — paste `/status` and correct this
table if it disagrees.
The gateway URL and auth token are deliberately not recorded here — this repo
is public.

---

## 001 — 2026-10-15 — publish repo

**Model:** `agentic` / Claude Code 2.1.299

**Asked:** Create a public GitHub repo `mlr-agent-lab` from this folder with
`gh`, showing what would be uploaded before pushing.

**Checked:** Manifest shown and confirmed before the push — 2 files
(`hello.py`, `.gitignore`), with `.claude/settings.local.json` excluded as
machine-local. Flagged that the configured commit email was a university
address about to become public; switched to the GitHub noreply address,
repo-local only, global git config untouched. After pushing, verified against
the API rather than trusting the push message:

```
git ls-remote --heads origin   -> 82fee29  refs/heads/main
repo contents                 -> .gitignore, hello.py
repo visibility               -> {"private":false,"default_branch":"main"}
```

**Left open:** Commit email is the login-only noreply form, not the canonical
`<id>+<login>@...`. Links to the account only if that address is registered
under Settings → Emails.

## 002 — 2026-10-21 — working rules + docs

**Model:** `agentic` / Claude Code 2.1.299

**Asked:** Write `AGENTS.md` (read README + PLAN first, uv only, run checks
before claiming done), make `CLAUDE.md` load it, create `README.md`,
`PLAN.md`, `RUNS.md`.

**Checked:** Every command documented in `AGENTS.md` was run first, not
written from assumption — `uv run hello.py` prints `hello`; `uv add requests`
fails with `No pyproject.toml found`. The failure is documented rather than
hidden, and filed as the next step in `PLAN.md`. Import syntax and load
verification: see `AGENTS.md` rule 3 note.

**Left open:** Not committed, not pushed — the five files are on disk only.
Commit and push are waiting on you.
