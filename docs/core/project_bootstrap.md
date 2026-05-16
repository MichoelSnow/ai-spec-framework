# project_bootstrap.md

## Purpose
Defines the required initial setup for every new project.

This must be completed before implementing features.

---

## Required Files

- README.md
- .gitignore
- agents.md (in repo root)
- docs/core/ (with all control files)

---

## Environment Setup

- Define environment variables structure
- Create `.env.example`
- Ensure `.env` is in `.gitignore`
- If Python is used in the repo, explicitly choose the target Python version before dependency setup (agent must always ask the user which version to use)
- After Python version selection, use Poetry as the source of truth for dependency compatibility:
  - Set interpreter: `poetry env use <python-version>`
  - Add/update dependencies using latest candidates (for example `poetry add ...@latest`)
  - Resolve/validate via Poetry lock/install; treat solver failures as compatibility constraints to address explicitly

---

## Git Setup

- Initialize repository
- Set default branch (main)
- Make initial commit

---

## CI / Quality Gates

- Configure CI pipeline
- Include:
  - linting
  - tests
  - gitleaks
- CI must run on every PR

---

## Tooling

- Configure formatter/linter 
  - Use Ruff for Python
  - Use ESLint for JavaScript/TypeScript
- Configure package manager
  - Use pnpm instead of npm or yarn
  - Use poetry for python
- Resolve dependency versions from live official registries at implementation time (for example npm and PyPI); do NOT pin versions from memory
- Prefer current stable releases unless a project constraint requires otherwise; document any intentional pin/downgrade reason
- If JavaScript/TypeScript is used in the repo, explicitly choose the target Node version before dependency setup (agent must always ask the user which version to use)
- After Node version selection, use pnpm as the source of truth for dependency compatibility:
  - Set runtime baseline in repo (for example `.nvmrc` and `package.json` `engines.node`)
  - Create lockfile before upgrades: `pnpm install`
  - Update dependencies non-interactively: `pnpm up -Lr --save` (use `-w` when operating at workspace root)
  - Resolve/validate via install and project gates; treat failures as compatibility constraints to address explicitly
- Ensure consistent code style

---

## Testing Setup

- Set up test framework
  - Use pytest for Python
- Ensure tests can run locally and in CI

---

## Security Baseline

- Verify `.env` is ignored
- No secrets committed
- HTTPS assumed for all external communication

---

## Documentation

- Keep docs minimal and structured
- Do NOT create unnecessary files

---

## Enforcement

- Do not begin feature development until bootstrap is complete
- Missing setup = incomplete project
