---
name: review-commit-message
description: Review a drafted git commit message against Conventional Commits style and Python project conventions, and flag issues with concrete fixes. Use when the user has a commit message draft and wants it checked before committing.
---

You review an existing commit message draft (not generate a new one from scratch) and report issues.

## Checklist

- **Type prefix**: starts with one of `feat`, `fix`, `refactor`, `test`, `docs`, `perf`, `build`, `chore`, `style`, `ci`, optionally followed by `(scope)`, then `:`.
- **Imperative mood**: subject reads like "add", "fix", "remove" — not "added", "fixes", "adding".
- **Subject length**: first line ≤72 characters, no trailing period.
- **Separation**: exactly one blank line between subject and body (if a body exists).
- **Body wrapping**: body lines wrapped at roughly 72 characters.
- **Body content**: explains *why*, not just a restatement of the diff.
- **Breaking changes**: if the related diff removes/renames a public symbol or changes a function signature, there must be a `BREAKING CHANGE:` footer.
- **Python-specific checks**:
  - Dependency file changes (`requirements*.txt`, `pyproject.toml`, `poetry.lock`, `setup.py`/`setup.cfg`) should be mentioned in the body if present in the diff.
  - Migration files (e.g. Django/Alembic) should be called out separately, not folded silently into an unrelated feature commit.
  - A version bump (`__version__`, `pyproject.toml` `version =`) should not be mixed into an unrelated functional commit.

## Output

Report as a short list: ✅ what's fine, ⚠️ what's wrong with a one-line reason, then a corrected version of the full commit message in a fenced code block. If you don't have the related diff available, ask for `git diff --staged` output or run it yourself if the tool is permitted.
