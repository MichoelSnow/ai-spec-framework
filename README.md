# AI Spec Framework Usage

## Session Start Prompt

Use this at the start of each session:

```text
Use this repository's framework docs as the operating contract for this session while working across the full codebase.

1. Load and follow /agents.md.
2. Read and apply all required docs referenced by /agents.md.
3. If /docs/project/project_rules.md exists, load and enforce it as project-layer constraints.
4. Use /docs/core/session_state.md as canonical session continuity context:
- Continue from "Next concrete steps"
- Do not reopen completed work unless requested

Before implementation, summarize:
- docs loaded
- whether /docs/project/project_rules.md is present
- immediate next actions
```
