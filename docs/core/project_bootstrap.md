# project_bootstrap.md

## Operating Rules

Complete this checklist before feature development:

- Repository contains: `README.md`, `.gitignore`, `agents.md`, and required `docs/core/*` files.
- Environment template exists as `.env.example`.
- `.env` is ignored by git.
- Default branch is `main`.
- CI runs on pull requests.
- CI includes linting and tests.
- CI includes secret scanning (for example `gitleaks`).
- Required linters/formatters are configured for languages used in the repo.
- Use `ruff` for Python repos.
- Use `eslint` for JavaScript/TypeScript repos.
- Use `pnpm` for JavaScript/TypeScript dependency management.
- Use `poetry` for Python dependency management.
- Select target Node version before Node dependency setup.
- Select target Python version before Python dependency setup.
- Required test framework is configured and runnable locally.
- Use `pytest` for Python repos.
- Resolve dependency compatibility through the selected package manager and lockfile before feature work.
- No feature work starts until all bootstrap checklist items pass.
