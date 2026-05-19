# application_rules.md

## Design System

- Use the project's standard UI component system (default: Tailwind + shadcn/ui).
- Reuse existing components before creating new ones.
- Keep one consistent design style across the application.
- Constrain primary page content to centered layouts with max width around 1200px unless explicitly required.
- Each page must have a clear primary purpose and primary action.
- Prefer progressive disclosure: show essential information first; hide secondary detail behind interactions.
- Do not render internal/system fields in UI (IDs, foreign keys, raw backend/debug metadata).
- Transform backend data into user-facing labels and formats before display.
- Keep forms readable with constrained widths (roughly 400-600px on large screens).
- Preserve clear visual hierarchy for typography, spacing, and action emphasis.
- Maintain responsive behavior without collapsing information hierarchy.

## UI Scaffold

- Build every page with these primitives: `PageLayout`, `PageHeader`, `Section`, `FormContainer`, `Stack`.
- `PageLayout` must be the page root.
- `PageHeader` must appear at the top of each page and include a title.
- Use `Section` for all logical content groupings.
- Wrap all forms in `FormContainer`.
- Use `Stack` for vertical spacing.
- Do not build page structure from raw containers when a scaffold primitive applies.
- Do not introduce new layout primitives without updating this document.


## UI Patterns

- Before implementation, each page must be assigned exactly one pattern from this file.
- If no pattern fits, define and approve a new pattern before implementation.

### Pattern: List

Required structure:
1. `PageLayout`
2. `PageHeader` (title, optional description, primary action)
3. Primary `Section` with collection content
4. Optional secondary `Section` for filters/summary

Checks:
- Use consistent item structure.
- Limit visible item fields.
- Provide empty state behavior.

### Pattern: Form

Required structure:
1. `PageLayout`
2. `PageHeader`
3. `Section` containing `FormContainer`

Checks:
- Show required fields first.
- Keep advanced fields secondary/optional.

### Pattern: Detail

Required structure:
1. `PageLayout`
2. `PageHeader`
3. Summary `Section`
4. Optional secondary `Section` blocks

Checks:
- Prioritize key information.
- Group related details.

### Pattern: Canvas / Workspace

Required structure:
1. `PageLayout`
2. `PageHeader`
3. Controls `Section`
4. Canvas/workspace `Section`

Checks:
- Canvas/workspace is the dominant element.
- Controls remain compact and secondary.
- Do not mix large forms/lists into the canvas area.
- Do not display raw timestamps, debug output, IDs, or other internal/system fields in canvas-adjacent UI.

### Pattern: Empty State

Required elements:
- Clear no-data message
- Short explanation
- Primary next action

### Pattern: Modal / Focused Interaction

Checks:
- Scope is small and contained.
- Use for focused secondary actions, not primary navigation.