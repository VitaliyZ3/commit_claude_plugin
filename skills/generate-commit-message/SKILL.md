---
name: generate-commit-message
description: Generate a Conventional Commits style commit message for staged Python changes by analyzing the git diff. Use when the user wants help writing a commit message for Python code changes.
allowed-tools: Bash(git *)
---

You write a commit message for the currently staged changes in a Python project.

## Steps

1. Run `git diff --staged --stat` and `git diff --staged` to see what changed. If nothing is staged, fall back to `git diff` and tell the user you're using unstaged changes.
2. Classify the change into a Conventional Commits type:
   - `feat` – new functionality
   - `fix` – bug fix
   - `refactor` – code change that doesn't fix a bug or add a feature
   - `test` – only test files changed (e.g. `tests/`, `test_*.py`, `*_test.py`)
   - `docs` – only docs/comments/README/docstrings changed
   - `perf` – performance improvement
   - `build`/`chore` – tooling, `pyproject.toml`, `requirements*.txt`, CI config, packaging
3. Pick a short `scope` from the top-level package or module most affected (e.g. the first path segment under `src/` or the module name), omit it if the change is repo-wide.
4. Write the message:
   - Subject line: `type(scope): summary` in imperative mood, lowercase, no trailing period, ≤72 characters.
   - Blank line, then a body explaining *why* the change was made (not just what), wrapped at ~72 characters per line.
   - If `requirements*.txt`, `pyproject.toml`, or `poetry.lock` changed, call out the dependency change explicitly in the body.
   - If the diff changes a public function/class signature or removes something importable, add a footer: `BREAKING CHANGE: <description>`.
5. Output the final commit message in a fenced code block, ready to paste into `git commit -m`. Do not run `git commit` yourself unless the user explicitly asks you to commit.
