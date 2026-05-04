# Contributing to STRIZH

## Branch Structure

```
main  -- production-ready. PR from dev only. Direct push forbidden.
  dev -- integration branch. PR from feature/fix/chore/refactor only.
        feature/<name>
        fix/<name>
        chore/<name>
        refactor/<name>
```

All work happens in a dedicated branch created from `dev`.

---

## Starting a Task

```bash
git checkout dev
git pull origin dev
git checkout -b feature/task-name
```

---

## Branch Naming

| Prefix | When to use |
|--------|-------------|
| `feature/` | New functionality |
| `fix/` | Bug fix |
| `chore/` | Infrastructure, dependencies, config |
| `refactor/` | Refactoring without behavior change |
| `docs/` | Documentation |

Examples:
```
feature/auth-login-endpoint
feature/confluence-page-fetch
fix/jwt-token-expiry
chore/docker-compose-setup
```

---

## Commits - Conventional Commits

Format: `<type>(<scope>): <what was done>`

| Type | When |
|------|------|
| `feat` | New functionality |
| `fix` | Bug fix |
| `chore` | Infrastructure, dependencies |
| `refactor` | Refactoring |
| `test` | Tests |
| `docs` | Documentation |

Examples:
```
feat(auth): add JWT login endpoint
fix(generation): handle empty LLM response
chore(infra): add MongoDB and Redis to docker-compose
test(auth): add unit tests for bcrypt hashing
docs(api): update OpenAPI description for /generate
```

---

## Pull Request Rules

1. PR goes from your branch to **`dev`** (not to `main`)
2. PR title follows Conventional Commits format
3. Description: what was done and how to verify
4. CI must pass: lint + type check + tests + docker build
5. **1 approval** required from the second developer
6. Merge: **Squash and merge**
7. Delete branch after merge

---

## Merging dev into main

- PR with approval only
- **Merge commit** (not squash) - preserves history
- Only after testing on dev environment
- Tag the version: `v0.1.0`, `v0.2.0`, etc.

```bash
git tag v0.1.0
git push origin v0.1.0
```

---

## Hotfix - urgent production fix

```bash
git checkout main
git pull origin main
git checkout -b hotfix/problem-description

# Fix, commit, push
git push origin hotfix/problem-description

# Open PR to main (with approval)
# After merging to main -- MUST also merge into dev
```

---

## Prohibited

- Direct push to `main` or `dev`
- `git push --force` to `main` or `dev`
- Merge without approval
- Merge when CI fails
- Committing secrets, passwords, `.env` files
