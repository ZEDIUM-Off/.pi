# Security policy

This repository is public configuration only.

If a token, cookie, session transcript, private project path, or proprietary snippet is committed by mistake:

1. revoke or rotate the exposed credential immediately;
2. remove it from Git history before pushing or while the repository is still private;
3. verify with `git grep` and a secret scanner such as `gitleaks`.

Known local-only Pi files are excluded in `.gitignore`, especially `agent/auth.json`, `agent/sessions/`, `agent/run-history.jsonl`, `agent/git/`, `agent/bin/`, and `pi-acp/`.
