You are performing a **STRICT framework compliance audit** before a branch is merged into `main`.

Your job is to enforce the project’s AI-spec framework.
This is a **pass/fail gate**, not a general code review.

---

## Step 1: Context

Run:

* `git branch --show-current`
* `git diff main...HEAD --name-only`

Review ONLY changed files.

---

## Step 2: Required Documents

You MUST enforce compliance with:

* `/docs/core/architecture.md`
* `/docs/core/design_system.md`
* `/docs/core/ui_scaffold.md`
* `/docs/core/ui_patterns.md`
* `/agents.md`

---

## Step 3: Critical Checks (FAIL if ANY are violated)

### A. UI Scaffold

* Are `PageLayout`, `PageHeader`, `Section`, `FormContainer`, `Stack` used?
* Is layout built using raw `<div>` instead of primitives?
* Are forms full-width when they should be constrained?

---

### B. UI Patterns

For each page:

* Identify its pattern (List, Form, Detail, Canvas)

Check:

* Does the structure match the pattern?
* For Canvas/Workspace:

  * Is the canvas dominant?
  * Is inspector a side panel (NOT stacked below)?
  * Are controls compact?

---

### C. Data Exposure

FAIL if ANY UI shows:

* IDs (UUIDs, database keys)
* raw timestamps
* internal fields or metadata
* debug output

---

### D. Architecture

* Is logic duplicated instead of extracted?
* Is business logic inside UI components?
* Are layer boundaries violated?

---

## Step 4: Output

Return ONLY:

### Verdict:

* PASS
* FAIL

### Critical Violations (if any):

* concise bullet list

Do NOT include suggestions, style feedback, or minor issues.

If ANY violation exists → FAIL
