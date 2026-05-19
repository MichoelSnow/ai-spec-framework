# application_rules.md

## Design Rules

- Use the project UI component system consistently (default: Tailwind + shadcn/ui).
- Reuse existing components before creating new ones.
- Keep one consistent visual style across the application.
- Constrain primary page content to centered layout with max width around `1200px` unless explicitly required.
- Each page must have one clear primary purpose and primary action.
- Apply progressive disclosure: show essential information first; keep secondary detail behind interactions.
- Do not render internal/system fields in UI (IDs, foreign keys, raw backend/debug metadata, raw timestamps).
- Transform backend data into user-facing labels and formats before display.
- Keep forms constrained to readable width (roughly `400-600px` on large screens).
- Maintain responsive behavior without collapsing hierarchy.

## Scaffold Rules

- Build every page with primitives: `PageLayout`, `PageHeader`, `Section`, `FormContainer`, `Stack`.
- `PageLayout` must be the page root.
- `PageHeader` must appear at the top of each page and include a title.
- Use `Section` for each logical content grouping.
- Wrap forms in `FormContainer`.
- Use `Stack` for vertical spacing.
- Do not build page structure from raw containers when a scaffold primitive applies.
- Do not introduce new layout primitives without updating this file.

## Pattern Rules

- Assign exactly one page pattern before implementation: `List`, `Form`, `Detail`, `Canvas/Workspace`, `Empty State`, or `Modal/Focused Interaction`.
- If no pattern fits, define and approve a new pattern before implementation.
- `Canvas/Workspace` pages must keep the canvas dominant and controls secondary.
- Pattern implementation details and structural checklists live in `/docs/reference/application_ui_guidance.md`.
