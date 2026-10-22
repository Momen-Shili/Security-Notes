# Secrets and configuration

**Risk:** leaked API keys, database passwords and signing keys, usually through Git history.

## Rules
- Keep secrets out of Git. Use environment variables or a secret manager, and commit only a `.env.example` with fake values.
- Add `.env` and key files to `.gitignore` before the first commit.
- **If a secret was ever committed, rotate it.** Deleting it in a later commit does not remove it from history.
- Run a secret scanner (for example gitleaks or GitHub secret scanning) in CI and as a pre-commit hook.
- Use separate secrets per environment, and the least privilege per key.
- Rotate keys on a schedule and when someone leaves.
- Debug mode, verbose errors, default admin accounts and open admin panels must be off in production.
- Never log tokens, passwords or full request bodies.

## Public repos
Before making a repo public, search the history, not just the current files.
