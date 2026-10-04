# UI Patterns and Examples

## Design intent

Clear hierarchy, focused screens, progressive disclosure, and user-facing data can help make interfaces understandable without exposing internal system shape.

Each page should have one clear primary purpose and primary action.

## Layout guidance

- Responsive layouts should preserve information hierarchy rather than merely shrinking or compressing a desktop layout.
- Primary reading content and forms should remain at a readable measure on large screens rather than expanding unnecessarily across the available width.

User-facing interfaces should generally favor user-facing labels and formats over raw IDs or foreign keys, raw payloads, debug metadata, or unexplained timestamps.

## Progressive disclosure guidance

- Primary actions and essential data are often most useful at the start.
- Advanced controls can be placed behind modals, tabs, drawers, or secondary sections.
- Multiple focused screens may be preferable to a single dense surface.

## Pattern usage guidance

- List pages should prioritize scanability and consistent item structure.
- Form pages should optimize completion speed and reduce cognitive burden.
- Detail pages should separate summary from secondary information.
- Canvas pages should prioritize the workspace while keeping controls compact.

## Consistency guidance

- Reusing established primitives and component patterns can support consistency.
- Consistent spacing and typography scales may improve coherence.
- Avoiding style mixing across pages and features can reduce visual friction.

## Pattern structures and considerations

The component names and structures shown below are illustrative. Projects should prefer their established equivalents and should not introduce new UI primitives solely to match these examples.

### List Pattern

Possible structure:
1. `PageLayout`
2. `PageHeader`
3. Primary `Section` with collection content
4. Optional secondary `Section` for filters/summary

Considerations:
- Consistent item structure can improve scanability.
- A limited set of visible fields can keep the collection focused.
- Empty-state behavior is useful when the collection has no items.

### Form Pattern

Possible structure:
1. `PageLayout`
2. `PageHeader`
3. `Section` containing `FormContainer`

Considerations:
- Showing required fields first can support completion.
- Advanced fields can remain secondary or optional.

### Detail Pattern

Possible structure:
1. `PageLayout`
2. `PageHeader`
3. Summary `Section`
4. Optional secondary `Section` blocks

Considerations:
- Prioritizing key information can make details easier to use.
- Grouping related details can clarify the summary.

### Canvas / Workspace Pattern

Possible structure:
1. `PageLayout`
2. `PageHeader`
3. Controls `Section`
4. Canvas/workspace `Section`

Considerations:
- A dominant canvas or workspace can keep the main task prominent.
- Compact, secondary controls can preserve workspace focus.
- Keeping large forms and lists outside the canvas area may reduce distraction.

## State handling guidance

- Loading, error, and insufficient-data states should preserve the page's purpose and, where appropriate, provide a useful next action.

### Empty State Pattern

Useful elements may include:
- Clear no-data message
- Short explanation
- Primary next action

### Modal / Focused Interaction Pattern

Considerations:
- Scope is small and contained.
- Focused secondary actions may be suitable for this pattern, while primary navigation may be better served elsewhere.

## Visualization guidance

- Charts and visualizations should clarify a comparison, pattern, or conclusion.
- Labels, legends, or takeaways should make the visualization understandable without requiring knowledge of internal terminology.
