# pipeline_rules.md

## Operating Rules

- Implement pipeline flow as explicit sequential stages (for example: load -> process -> evaluate -> store).
- Keep core execution readable in one pass.
- Do not split simple pipeline logic across many files.
- Introduce supporting modules only when reuse or clear separation is required.
- Do not introduce abstraction layers before stable duplication exists.
- Define inputs and outputs explicitly at each stage.
- Keep data transformations explicit and traceable.
- Control non-determinism with explicit seeding/configuration when randomness is required.
- Log stage boundaries and critical execution outcomes.
- Minimize dependencies; avoid heavy frameworks without clear necessity.
