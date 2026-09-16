# architecture_examples.md

## Optional layer mapping examples

Projects may map logical responsibilities to different folders when that helps clarity.

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

## Mapping considerations

- A stable mapping can reduce ambiguity.
- Folder names that make responsibility obvious can help future contributors.
- Choose structure according to the actual project; these examples are not framework requirements.
