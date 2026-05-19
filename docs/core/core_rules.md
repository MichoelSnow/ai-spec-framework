# core_rules.md

## Overview

- Follow documented rules; do not invent structure when constraints already exist.
- Prefer the simplest implementation that satisfies requirements.
- Keep logic explicit; avoid hidden behavior and implicit side effects.
- Prefer deterministic behavior; control and document any required non-determinism.
- Do not generalize early; extract abstractions only after stable duplication exists.
- Follow the selected mode rules and do not mix mode contracts.
- Reuse existing project patterns before introducing new ones.
- Reject changes that increase complexity without reducing ambiguity.

## Architecture

- Organize code into these logical layers: Interface, Application, Domain, Shared.
- Define and maintain a project-specific folder mapping for these layers before feature work.
- Do not create new top-level directories without updating the layer mapping.
- Place each file in exactly one layer based on responsibility.
- Interface layer may depend only on Application and Shared.
- Application layer may depend only on Domain and Shared.
- Domain layer must not depend on Interface or Application.
- Shared layer must not depend upward on Interface/Application/Domain-specific code.
- Keep business logic out of Interface and Shared layers.
- When stable duplication appears, extract shared logic instead of copy-paste.
- Remove replaced or duplicate implementations as part of the same change.

## Documentation

- Do not create new documentation files unless requested or required by this framework.
- Update existing docs instead of creating overlapping documents.
- Keep one clear responsibility per document.
- All control documents that constrain agent behavior must live under `/docs/core/` unless explicitly defined as mode docs under `/docs/modes/`.
- Do not duplicate rules across documents; reference the source document.
- Keep operating docs concise and actionable.
- When behavior changes, update affected documentation in the same change.
- Remove or correct outdated documentation.
- `docs/project/project_rules.md` is optional and must only contain project-specific additions or stricter constraints.

## Security

- Validate, sanitize, and schema-validate all external input; reject unexpected payloads.
- Enforce authentication and authorization on protected operations, including role/permission checks.
- Do not build custom authentication mechanisms when established libraries are available.
- Use HTTPS for external communications.
- Apply strict CORS in production; do not use wildcard origins.
- Apply rate limiting on public endpoints.
- Do not hardcode secrets or credentials; use managed or environment-based secret/key management.
- Do not commit `.env` files; keep `.env.example` with placeholder values only.
- Use secure password hashing (bcrypt or Argon2) where passwords are stored.
- Enforce secure session controls (expiration, rotation, invalidation).
- If JWT is used, enforce expiration and signature/claim validation.
- Use parameterized queries or safe ORM patterns for database access.
- Encrypt sensitive data in transit and at rest.
- Do not expose sensitive data in logs, errors, or API responses; return generic client-facing errors.
- Enforce secure cookie/session settings for authenticated web sessions (`HttpOnly`, `Secure`, `SameSite`).
- Enable CSRF protection for state-changing browser requests.
- Enable baseline browser security headers (`CSP`, `HSTS`, `X-Frame-Options`, `X-Content-Type-Options`).
- Default to secure configuration (fail closed) and disable debug modes in production.
- Define and enforce data retention rules for stored sensitive data.
- Keep dependencies maintained and patch known critical vulnerabilities before merge.
- Include security tests for auth, authorization, input validation, and failure-mode handling on changed security-sensitive paths.

## Testing

- Every new function, behavior change, or bug fix must include tests, including regression coverage for fixes.
- Work is incomplete unless required tests exist and pass.
- Required tests must cover normal, edge, and failure behavior for changed logic.
- Add integration tests for changed API, database, or multi-step workflow behavior.
- Add smoke tests for new workflows and CLI commands.
- If a required test cannot be run, document the reason and provide manual verification steps.
- Tests must be deterministic, isolated, and repeatable.
