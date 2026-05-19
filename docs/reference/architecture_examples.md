# architecture_examples.md

## Layer mapping examples

Projects can map the required logical layers to different folders.

Frontend example:
- Interface: page and route entrypoints
- Application: feature-level orchestration
- Domain: business rules and entities
- Shared: reusable components and utilities

Backend example:
- Interface: API/CLI adapters
- Application: use-case orchestration
- Domain: core business logic
- Shared: cross-cutting helpers

## Mapping guidance

- Keep mapping stable once established.
- Update mapping before introducing new top-level structure.
- Prefer folder names that make layer responsibility obvious.
