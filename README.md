# AI Spec Framework

The framework separates universal behavior from project facts, scoped correctness requirements, task procedures, and optional reference material.

- [`AGENTS.md`](AGENTS.md) is the small always-on contract.
- [`docs/project_context.md`](docs/project_context.md) records relevant project facts and accepted decisions.
- [`docs/requirements/`](docs/requirements/) contains binding requirements that apply only to stated subsystems.
- [`docs/reference/`](docs/reference/) contains non-binding patterns, examples, rationale, and history.

Task-specific skills are maintained in a separate skills repository and are not duplicated here.


## Session Start Prompt

Use this at the start of a session when you want the agent to explicitly establish project context before working:

```text
Use this repository's framework as the operating context for this session.

1. Load and follow /AGENTS.md.
2. Read /docs/project_context.md if project characteristics are relevant to the current task.
3. Identify and load any applicable scoped requirements under /docs/requirements/.
4. If I explicitly ask to resume from a handoff/session-state file, load and use that file. Do not read or update session-state files automatically.
5. Use relevant shared skills for task-specific procedures.
6. Treat /docs/reference/ as non-binding guidance unless an applicable scoped requirement explicitly adopts it.

Before implementation, briefly summarize:
- framework/context loaded,
- applicable scoped requirements,
- relevant skills,
- any material uncertainty,
- immediate next action.

Do not modify files until the current request explicitly authorizes implementation.
```
## New Project Start Prompt


Read `AGENTS.md` and `docs/bootstrap.md`.

I am starting a new project from scratch.

The basic project idea is:

[DESCRIBE THE PROJECT HERE]

Use the bootstrap process to take this repository from a framework-only state to an initial usable project.

Start by asking me the decision-relevant questions needed to establish the project context and initial repository shape. Ask only a few questions at a time, and do not ask about decisions that can reasonably wait until later development.

Use my answers to determine:

- the initial `docs/project_context.md`;
- any scoped requirements that are already necessary to define correct initial behavior;
- the initial repository structure;
- language, runtime, and package-management choices;
- testing and quality tooling;
- Git and CI setup;
- persistence or database setup when applicable;
- environment/configuration structure;
- deployment configuration only when already justified by the project.

Do not create or modify files yet.

Once the material bootstrap decisions are resolved, show me the proposed project context, initial requirements, repository tree, and important tooling choices for approval.

Wait for my approval before creating the scaffold.

Do not run commands or other executable workflows unless I separately authorize execution.