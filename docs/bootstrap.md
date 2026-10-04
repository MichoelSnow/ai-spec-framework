# Repository Bootstrap

## Purpose

This document defines the initial repository bootstrap process after the framework files have already been copied into a new project.

Bootstrap creates the non-framework foundation needed before normal feature development begins.

It should establish the smallest practical repository scaffold for the actual project while applying the standard repository, Git, quality, security, and CI conventions used across projects.

Bootstrap is interactive. Do not silently make material project-shaping decisions when the user's input would materially affect the resulting repository.

---

## Inputs

Before bootstrapping, use:

- `AGENTS.md`
- `docs/project_context.md`
- any applicable initial documents under `docs/requirements/`
- the user's description of the intended project
- decisions already established in the current conversation

Do not ask the user to repeat information already available from these sources.

---

## Clarification Before Scaffolding

Before creating non-framework project files, identify unresolved decisions that materially affect the initial repository.

Relevant questions may include:

- primary language or languages;
- target Python version;
- target Node version;
- application, library, service, data, or mixed-project shape;
- frontend/backend boundaries;
- persistence or database needs;
- analysis or notebook needs;
- deployment target;
- environment/configuration requirements;
- testing needs that differ from the standard defaults;
- unusual CI/CD requirements;
- monorepo versus single-package structure.

Ask only decision-relevant questions.

Prefer 1–3 questions per round rather than presenting a large questionnaire.

If two or more reasonable choices would materially change the repository structure, dependencies, deployment model, or maintenance burden, ask the user rather than choosing silently.

For low-impact, reversible decisions that fit established project defaults, choose the simplest reasonable option and state the assumption.

### Required runtime questions

If Python will be used, explicitly ask the user which Python version to target unless it has already been established.

If JavaScript or TypeScript will be used, explicitly ask the user which Node version to target unless it has already been established.

---

## Scaffold Checkpoint

Before creating a substantial scaffold, briefly show the proposed repository structure and important tooling choices.

The proposal should identify:

- major directories;
- package/runtime configuration;
- testing setup;
- CI/CD setup;
- database or persistence structure if applicable;
- deployment-related files if applicable;
- any material assumptions.

Resolve material disagreements before proceeding.

Do not create speculative directories or infrastructure for hypothetical future needs.

---

## Universal Repository Baseline

Create the baseline files appropriate to essentially every project:

```text
README.md
.gitignore
.gitattributes
.editorconfig
.env.example
.github/
  workflows/
```

Retain the framework files already present.

Do not recreate, relocate, or duplicate framework documentation during bootstrap.

Additional baseline files such as `LICENSE` may be added when applicable.

---

## README

Create an initial `README.md` that reflects the project as it currently exists.

At minimum, include:

- project name;
- concise purpose;
- current project status;
- major technology choices;
- basic repository structure where useful;
- development/setup instructions that are already known;
- testing instructions once established.

Keep the README useful but minimal.

Do not invent future capabilities merely to make the README appear complete.

---

## Environment Configuration

Create `.env.example` when the project may require environment variables.

Ensure:

- `.env` and local environment variants are ignored;
- example files contain placeholders rather than secrets;
- required environment variables are documented sufficiently for local setup;
- secrets are never committed.

Do not create unnecessary environment-variable infrastructure for projects that do not need it.

---

## Language and Package Tooling

Configure only the language ecosystems actually used by the project.

### Python

Default Python project tooling:

- `pyproject.toml`
- Poetry for dependency and environment management
- Ruff for linting and formatting
- pytest for testing

Before dependency setup, establish the user-selected Python version.

Use Poetry as the source of truth for dependency compatibility.

When dependency operations are authorized:

- use the selected interpreter;
- resolve dependency versions against current package registry information rather than memory;
- prefer current stable releases unless a project constraint requires otherwise;
- document intentional pins or downgrades;
- treat dependency-solver failures as compatibility constraints to resolve explicitly.

Do not add dependencies solely because they are commonly used.

### JavaScript / TypeScript

Default JavaScript/TypeScript tooling:

- `package.json`
- pnpm rather than npm or Yarn
- ESLint
- appropriate test tooling for the selected framework/project

Before dependency setup, establish the user-selected Node version.

Record the runtime baseline appropriately, such as with:

- `.nvmrc`;
- `package.json` `engines.node`.

Use pnpm as the dependency source of truth.

When dependency operations are authorized:

- resolve versions against current official registry information;
- prefer current stable releases unless constrained;
- create and retain the lockfile;
- document intentional pins or downgrades.

### Mixed repositories

When both ecosystems are genuinely required, configure both without forcing either ecosystem to own concerns belonging to the other.

---

## Project Structure

Create only directories supported by the accepted project shape.

Examples may include:

```text
src/
tests/
apps/
packages/
analysis/
scripts/
migrations/
data/
```

These names are examples, not a required taxonomy.

Prefer the smallest structure that cleanly supports the project's known responsibilities.

Do not create empty architecture for anticipated future services, packages, layers, or applications.

Nested `AGENTS.md` files should be created only where genuinely scoped behavior justifies them.

---

## Analysis and Data Projects

When analysis or notebooks are a first-class part of the project, create an appropriate analysis area rather than mixing exploratory artifacts with production code.

Where relevant, distinguish:

- source ingestion;
- exploratory analysis;
- reusable transformations;
- feature engineering;
- modeling;
- production/application logic.

Do not introduce complex data infrastructure before the project requires it.

Large generated datasets and local databases should normally remain outside version control.

---

## Database and Persistence Setup

If persistence is part of the initial project:

- establish the chosen database technology;
- create the minimal schema/migration structure needed;
- define local configuration expectations;
- ensure credentials remain external to version control.

Do not introduce a database merely because one might eventually be useful.

Do not create elaborate migration, ORM, warehouse, or orchestration infrastructure before justified by the current project.

---

## Git Setup

Every project should be prepared for normal Git-based development.

The intended baseline is:

- Git repository initialized;
- default branch is `main`;
- appropriate `.gitignore`;
- `.gitattributes`;
- initial repository state committed after bootstrap is complete.

Protect existing Git history and uncommitted work.

Never discard, overwrite, reset, or clean unrelated user work.

Git commands are executable actions and require explicit execution authorization under `AGENTS.md`.

Do not interpret authorization to create bootstrap files as authorization to:

- run `git init`;
- stage files;
- create commits;
- change branches;
- add remotes;
- push.

Ask for execution authorization when those actions become necessary.

---

## CI and Quality Gates

Configure GitHub Actions CI unless the project explicitly uses another CI system.

The standard CI baseline should include the applicable equivalents of:

- linting;
- formatting validation;
- tests;
- gitleaks secret scanning.

CI should run on pull requests.

Where appropriate, it may also run on pushes to `main`.

Language-specific CI should use the same runtime versions and package-management approach established for local development.

Avoid duplicate quality systems that provide substantially the same check.

---

## Testing Setup

Every code project should have a usable testing foundation appropriate to its language and project type.

For Python, use pytest by default.

For JavaScript/TypeScript, select the testing framework appropriate to the chosen application/framework rather than adding one blindly.

The initial scaffold should make it clear:

- where tests live;
- how tests are run;
- how CI invokes them.

Do not create large placeholder test suites merely to populate the repository.

---

## Security Baseline

At bootstrap:

- ensure secrets and local environment files are ignored;
- include gitleaks in CI;
- do not place credentials, tokens, or private keys in repository files;
- use secure external communication defaults where applicable;
- expose only configuration that is safe to commit.

Additional security controls should remain proportional to the project's actual exposure and data sensitivity.

Do not introduce enterprise security infrastructure without a concrete requirement.

---

## CI/CD and Deployment

CI is part of the standard project baseline.

Deployment configuration is created when a deployment target is known or deployment is part of the initial project shape.

When deployment is applicable:

- use the selected hosting/platform conventions;
- keep deployment configuration minimal;
- keep secrets outside the repository;
- separate validation CI from deployment actions where practical;
- avoid speculative multi-environment or enterprise release machinery.

If the deployment target has not been chosen and the choice materially affects the scaffold, ask the user.

---

## Dependency and Tool Version Resolution

Do not choose current package versions from model memory.

When dependency configuration requires current versions, resolve them from authoritative package registries or official project sources at implementation time.

Prefer current stable releases unless:

- the selected runtime constrains compatibility;
- another dependency requires a different version;
- the repository already has an established constraint;
- the user specifies otherwise.

Document intentional compatibility pins or downgrades when they would otherwise be surprising.

---

## Documentation

Keep documentation minimal and authoritative.

Bootstrap should create documentation needed to understand and operate the initial repository, not documentation for hypothetical future work.

Do not generate:

- duplicate architecture documents;
- generic process documents;
- exhaustive setup guides for unused tooling;
- placeholder documentation with no current informational value.

Project-specific facts belong in `docs/project_context.md`.

Binding subsystem rules belong in `docs/requirements/`.

Optional rationale and examples belong in `docs/reference/`.

Ordinary project documentation belongs in `docs/project/`.

---

## Execution Boundary

Bootstrap describes both file creation and executable setup actions, but those are separately authorized.

Authorization to bootstrap or create repository files does not itself authorize execution.

Before running commands such as:

```text
git init
git add
git commit
poetry install
poetry lock
poetry add
pnpm install
pnpm up
pytest
ruff
eslint
npm/pnpm scripts
database migrations
Docker commands
builds
deployments
cloud commands
```

obtain explicit execution authorization unless the current user request already provides it.

Read-only inspection remains allowed under the repository operating contract.

If required execution has not been authorized, complete the file/scaffold portion that is authorized and clearly identify the remaining bootstrap steps.

Do not claim bootstrap is fully validated when required executable validation has not been performed.

---

## Bootstrap Completion

Bootstrap is complete when the repository has the appropriate:

- baseline repository files;
- README;
- environment configuration;
- language/runtime configuration;
- package-management configuration;
- project directory structure;
- testing foundation;
- linting/formatting configuration;
- CI configuration;
- security baseline;
- persistence configuration when applicable;
- deployment configuration when applicable;
- Git setup when authorized.

Before normal feature development, summarize:

- what was created;
- important project/tooling decisions;
- what was verified;
- executable steps performed;
- executable steps not performed;
- anything intentionally deferred.

Do not treat intentionally unnecessary tooling as missing bootstrap work.

The goal is a clean, usable starting repository—not a maximally configured one.
