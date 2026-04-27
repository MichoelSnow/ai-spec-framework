# agents_pipeline.md

## Purpose
Defines the AI agent behavior for pipeline-style projects.

This profile is used for:
- evaluation pipelines
- scripts
- deterministic workflows
- research / experimentation code

This is NOT an application framework.

---

## Scope

You MUST follow only the relevant documents:

### Core (always required)
- /docs/core/architecture.md
- /docs/core/security_baseline.md
- /docs/core/testing_rules.md
- /docs/core/principles.md

### Pipeline Mode (required)
- /docs/modes/pipeline/pipeline_rules.md

### Explicitly NOT applicable
- design_system.md
- ui_scaffold.md
- ui_patterns.md

Do NOT reference or apply UI-related rules.

---

## Core Behavior

- Prefer simple, linear execution over abstraction
- Do NOT introduce layers unless necessary
- Do NOT split logic across multiple files prematurely
- Optimize for clarity and traceability

---

## Execution Model

- Code should be readable top-to-bottom in a single pass
- Prefer a single script unless complexity requires separation
- Avoid indirection (no unnecessary services, handlers, managers)

---

## Abstraction Rules

- Do NOT abstract unless duplication exists
- Do NOT generalize prematurely
- Refactor only when patterns are proven stable

---

## Determinism Requirements

- Inputs must be explicit
- Outputs must be reproducible
- Avoid hidden state
- Avoid non-deterministic behavior unless explicitly required

---

## Data Flow

- Data flow must be obvious and traceable
- Avoid implicit transformations
- Prefer explicit variable naming and step-by-step logic

---

## Dependency Rules

- Minimize dependencies
- Do NOT introduce libraries unless necessary
- Prefer standard library where possible

---

## Debugging & Transparency

- Code must be understandable without jumping across files
- Execution flow must be clear
- Avoid “magic” behavior or hidden logic

---

## Project-Specific Rules

If `/docs/project_rules.md` exists:

- You MUST read and apply it in addition to all other rules
- These rules are project-specific extensions of the current mode

### Precedence

If conflicts arise:

1. `/docs/project_rules.md` (highest priority)
2. Mode-specific rules (application or pipeline)
3. Core rules

### Constraints

- Project rules may restrict behavior further, but should not introduce unrelated systems
- Do NOT ignore core principles (e.g., clarity, determinism, simplicity)

If a conflict is unclear → choose the stricter interpretation

---

## Enforcement

If any implementation:
- introduces unnecessary abstraction
- obscures execution flow
- violates determinism

→ it is incorrect

---

## Guiding Principle

The framework should constrain complexity, not introduce it.
