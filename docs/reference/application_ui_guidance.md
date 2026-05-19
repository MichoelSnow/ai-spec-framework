# application_ui_guidance.md

## Design intent

Application mode favors clear hierarchy, focused screens, and progressive disclosure. The goal is to keep interfaces understandable without exposing internal system shape.

## Progressive disclosure guidance

- Start with primary actions and essential data.
- Move advanced controls behind modals, tabs, drawers, or secondary sections.
- Prefer multiple focused screens over a single dense surface.

## Pattern usage guidance

- List pages should prioritize scanability and consistent item structure.
- Form pages should optimize completion speed and reduce cognitive burden.
- Detail pages should separate summary from secondary information.
- Canvas pages should prioritize the workspace while keeping controls compact.

## Consistency guidance

- Reuse established primitives and component patterns.
- Keep spacing and typography scales consistent.
- Avoid style mixing across pages and features.

## Pattern structures and checks

### List Pattern

Required structure:
1. `PageLayout`
2. `PageHeader`
3. Primary `Section` with collection content
4. Optional secondary `Section` for filters/summary

Checks:
- Use consistent item structure.
- Limit visible fields.
- Provide empty-state behavior.

### Form Pattern

Required structure:
1. `PageLayout`
2. `PageHeader`
3. `Section` containing `FormContainer`

Checks:
- Show required fields first.
- Keep advanced fields secondary/optional.

### Detail Pattern

Required structure:
1. `PageLayout`
2. `PageHeader`
3. Summary `Section`
4. Optional secondary `Section` blocks

Checks:
- Prioritize key information.
- Group related details.

### Canvas / Workspace Pattern

Required structure:
1. `PageLayout`
2. `PageHeader`
3. Controls `Section`
4. Canvas/workspace `Section`

Checks:
- Canvas/workspace is dominant.
- Controls are compact and secondary.
- Do not mix large forms/lists into the canvas area.
- Do not display raw timestamps, debug output, IDs, or other internal/system fields in canvas-adjacent UI.

### Empty State Pattern

Required elements:
- Clear no-data message
- Short explanation
- Primary next action

### Modal / Focused Interaction Pattern

Checks:
- Scope is small and contained.
- Use for focused secondary actions, not primary navigation.
