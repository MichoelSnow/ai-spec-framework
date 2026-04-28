# 01_framework_audit.md

You are performing a **STRICT framework compliance audit** before a branch is merged into `main`.

Your job is to enforce the project’s AI-spec framework.
This is a **pass/fail gate**, not a general code review.

---

## scope

Only review files changed in:
`git diff main...HEAD`

---

## Step 1: Context

Run:

- `git branch --show-current`
- `git diff main...HEAD --name-only`

Review ONLY changed files.

---

## Step 2: Determine Mode

Identify which mode this project uses by inspecting:

- `/agents.md`
- referenced documents

### Modes

- **Application Mode**
  - References:
    - design_system.md
    - ui_scaffold.md
    - ui_patterns.md

- **Pipeline Mode**
  - References:
    - pipeline_rules.md

If unclear:
- infer from codebase structure
- choose the stricter interpretation

---

## Step 3: Required Documents

### Core (always enforce)
- `/docs/core/principles.md`
- `/docs/core/architecture.md`
- `/docs/core/security_baseline.md`
- `/docs/core/testing_rules.md`
- `/docs/core/docs_policy.md`

### Mode-Specific

#### Application Mode
- `/docs/modes/application/design_system.md`
- `/docs/modes/application/ui_scaffold.md`
- `/docs/modes/application/ui_patterns.md`

#### Pipeline Mode
- `/docs/modes/pipeline/pipeline_rules.md`

### Agent Rules
- `/agents.md`

---

## Step 4: Critical Checks (FAIL if ANY are violated)

### A. Core Compliance (ALWAYS)

- Is logic duplicated instead of extracted?
- Are architecture rules violated?
- Is code unnecessarily complex or over-abstracted?
- Does code violate core principles (clarity, determinism, simplicity)?
- Is execution flow difficult to understand?

---

### B. Mode-Specific Checks

#### If Application Mode:

##### B1. UI Scaffold

- Are required primitives used?
- Is layout built using raw `<div>` instead of primitives?
- Are forms incorrectly full-width?

##### B2. UI Patterns

For each page:

- Identify its pattern (List, Form, Detail, Canvas)

Check:

- Does the structure match the pattern?

For Canvas/Workspace:

- Is the canvas dominant?
- Is inspector a side panel (NOT stacked)?
- Are controls compact?

##### B3. Data Exposure

FAIL if ANY UI shows:

- IDs (UUIDs, database keys)
- raw timestamps
- internal fields or metadata
- debug output

---

#### If Pipeline Mode:

##### B4. Pipeline Rules

- Is logic unnecessarily split across multiple files?
- Is execution flow non-linear or hard to trace?
- Are abstractions introduced without duplication?
- Is logic hidden behind layers (services, handlers, executors)?
- Is behavior non-deterministic without justification?

---

### C. Project-Specific Rules

If `/docs/project_rules.md` exists:

- Are project-specific rules followed?

FAIL if violated.

---

## Step 5: Output

Return ONLY:

### Verdict:
- PASS
- FAIL

### Critical Violations (if any):
- concise bullet list

Do NOT include suggestions, style feedback, or minor issues.

If ANY violation exists → FAIL
