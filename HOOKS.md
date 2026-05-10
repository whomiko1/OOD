# Git hooks

This repo ships a tracked pre-commit hook in .githooks/ that blocks commits
to .obsidian/plugins/*/data.json (which typically contain API keys).

core.hooksPath is per-clone config and **not** tracked, so on any fresh
clone run once:

    git config core.hooksPath .githooks

Bypass for a single commit (only when you really mean it):

    git commit --no-verify