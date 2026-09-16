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