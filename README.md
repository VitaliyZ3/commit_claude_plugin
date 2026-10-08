# python-commit-messages

Claude Code plugin that helps write Conventional Commits-style commit messages for Python projects.

## Skills

- `generate-commit-message` — analyzes `git diff --staged` and drafts a commit message (type, scope, summary, body, breaking-change footer).
- `review-commit-message` — reviews an existing commit message draft against Conventional Commits and Python-specific conventions, and suggests a corrected version.

## Try it locally

```bash
claude --plugin-dir ./python-commit-plugin
```

Inside the session, type `/python-commit-messages:` to see both skills, or just describe what you need ("write a commit message for my staged changes") and Claude will pick the right one.
