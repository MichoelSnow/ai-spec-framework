# agents_pipeline.md

## Mode

- Active mode: Pipeline.
- Do not apply application UI rules to pipeline work.

## Required Operating Docs

Read and enforce before implementation:

- `/docs/core/core_rules.md`
- `/docs/core/session_state.md`
- `/docs/modes/pipeline/pipeline_rules.md`

## Agent Execution Priorities

### P0 - Blocking Rules

- Run a brief rule check before commands/edits; if blocked by a rule, stop and ask.
- State assumptions when they affect implementation.
- If multiple valid interpretations exist, present options instead of choosing silently.
- If scope or behavior is unclear, ask before implementing.
- Do not add speculative features, abstractions, or configurability.

### P1 - Strong Defaults

- Bias toward caution over speed; use judgment for trivial tasks.
- Prefer the minimum code that solves the requested problem.
- Keep changes surgical and directly traceable to the request.
- Do not refactor unrelated code.
- Remove only artifacts made unused by your own changes.
- For multi-step tasks, define explicit verification checks and run them.

### P2 - Hygiene Rules

- Remove dead or experimental code introduced by your own changes.
- Replace debug `print` usage with project-standard logging where applicable.
- Verify affected schema dependencies before applying schema-related changes.
- Use external tools only when required for the task.
- Do not use emojis in code.

## Pipeline Gate

Before implementing pipeline changes:

1. Keep execution flow explicit and sequential.
2. Keep core logic readable in one pass.
3. Avoid new abstraction layers unless stable duplication exists.

## Project Rules

- If `/docs/project/project_rules.md` exists, enforce it in addition to core and mode rules.

## Precedence

1. `P0` rules in this file
2. `/docs/project/project_rules.md`
3. Pipeline mode docs
4. `/docs/core/core_rules.md`
5. `P2` rules in this file

If conflict is unclear, apply the stricter rule and ask if needed.
