# pipeline_rules.md

## Purpose
Defines strict rules for pipeline-style projects.

This applies to:
- evaluation pipelines
- model benchmarking
- data processing scripts

---

## Core Principle

All logic must be:
- linear
- explicit
- easy to trace

---

## Execution Model

Preferred structure:

load → process → evaluate → store

Rules:
- Code must follow a clear step-by-step flow
- Avoid jumping between files for core logic
- A reader should understand the system in one pass

---

## File Structure

Allowed:
- single script (preferred)
- minimal supporting modules if necessary

Avoid:
- deep folder hierarchies
- unnecessary file splitting

---

## Abstraction Rules

- Do NOT abstract early
- Do NOT create layers unless duplication exists
- Keep logic inline until patterns stabilize

---

## Determinism

- All inputs must be defined explicitly
- Outputs must be reproducible
- Avoid randomness unless controlled and seeded

---

## Data Handling

- Avoid implicit transformations
- Use clear, descriptive variable names
- Each transformation step should be visible

---

## Logging

- Log key steps in execution
- Make pipeline progress observable
- Avoid excessive logging noise

---

## Dependencies

- Minimize external dependencies
- Prefer standard library
- Avoid complex frameworks

---

## Performance

- Keep pipelines efficient but prioritize clarity
- Avoid premature optimization

---

## Anti-Patterns (Do NOT do)

- Splitting simple logic into multiple files
- Creating service/handler/executor layers unnecessarily
- Hiding logic behind abstraction
- Introducing unnecessary frameworks
- Over-generalizing early

---

## Enforcement

If code:
- cannot be understood in one pass
- requires jumping across multiple files for basic logic
- introduces unnecessary abstraction

→ it is incorrect

---

## Guiding Principle

Clarity over abstraction. Determinism over flexibility. Simplicity over scale.
