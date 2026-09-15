# agents_application.md

## Mode

- Active mode: Application.
- Do not apply pipeline mode rules to application work.

## Required Operating Docs

Read and enforce before implementation:

- `/docs/core/core_rules.md`
- `/docs/core/session_state.md`
- `/docs/modes/application/application_rules.md`

## Interaction Rules

- Questions are non-mutating by default.
- If the user asks why, what, whether, how, should, or otherwise requests explanation, review, diagnosis, or critique, respond with text only.
- Do not edit files, run mutating commands, or apply fixes unless that same user message explicitly authorizes the change.
- Identifying an obvious mistake does not create authorization to fix it.
- Authorization from a previous implementation request does not carry forward to later question/review turns.
- If the user requests implementation, execute the change.
- Do not mix explanation and implementation unless requested.
- Keep responses concise unless more detail is requested.

## Mandatory Authorization Gate

Before every tool call, classify the user's latest message.

- Questions, explanations, reviews, diagnoses, status requests, comments, and objections are read-only.
- For read-only requests, do not edit, create, delete, rename, format, or regenerate files, and do not call write or patch tools.
- File modification is authorized only when the user explicitly requests an action such as edit, modify, change, fix, implement, apply, rewrite, or remove.
- Statements such as “should this be changed?”, “why did you leave this?”, “this is wrong”, or “please check” do not authorize modifications.
- A question about a previously completed task never implicitly authorizes a follow-up edit.
- If authorization is ambiguous, ask: “Would you like me to edit the file, or only explain the issue?”

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

## UI Gate

Before implementing UI changes:

1. Select a page pattern from `application_rules.md`.
2. Build using scaffold primitives defined in `application_rules.md`.
3. Enforce data-display constraints from `application_rules.md`.

## Project Rules

- If `/docs/project/project_rules.md` exists, enforce it in addition to core and mode rules.

## Precedence

1. `P0` rules in this file
2. `/docs/project/project_rules.md`
3. Application mode docs
4. `/docs/core/core_rules.md`
5. `P2` rules in this file

If conflict is unclear, apply the stricter rule and ask if needed.
