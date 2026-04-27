# agents_application.md

## Purpose
Defines the binding rules for AI agents working on application-style projects.

This profile applies to:
- UI-driven applications
- full-stack products
- long-lived systems

These rules override default agent behavior.

---

## Mode

This project uses **Application Mode**.

- UI, layout, and interaction rules are mandatory
- Do NOT apply pipeline-style simplification rules
- Do NOT ignore UI system constraints

---

## Control Files

You MUST read and follow:

### Core
/docs/core/principles.md
/docs/core/architecture.md
/docs/core/security_baseline.md
/docs/core/testing_rules.md
/docs/core/docs_policy.md
/docs/core/project_bootstrap.md
/docs/core/session_state.md

### Application Mode
/docs/modes/application/design_system.md
/docs/modes/application/ui_scaffold.md
/docs/modes/application/ui_patterns.md

---

## Relationship to Framework

This file defines the Application Mode profile.

- Core principles ALWAYS apply
- Application rules define structure and UI behavior
- Do NOT mix rules from other modes

If rules conflict:
- Application rules take precedence for UI and structure
- Core principles govern decision-making

---

## 1. Interaction Protocol (CRITICAL)

### 1.1 Response vs Execution

- If the user asks a question → respond with text only
- If the user gives a command → perform code changes only
- Ask clarifying questions before major changes
- Do NOT mix explanation and implementation unless explicitly requested

---

### 1.2 Output Control

- Keep responses concise by default
- Do NOT generate long explanations unless requested
- Do NOT generate large documents unless explicitly requested

---

## 2. Architecture Enforcement

- Follow architecture.md strictly
- Do NOT duplicate logic
- Extract shared logic into appropriate shared modules
- Respect layer boundaries

---

## 3. Design Enforcement (CRITICAL)

- Follow design_system.md strictly
- Do NOT invent UI styles or patterns
- Do NOT expose irrelevant data in UI
- Prefer minimal, structured layouts

---

## 4. UI Enforcement (CRITICAL)

- All UI MUST use primitives defined in ui_scaffold.md:
  - PageLayout
  - PageHeader
  - Section
  - FormContainer
  - Stack

- All pages MUST follow a pattern from ui_patterns.md

Before implementing UI:
1. Identify the correct page pattern
2. State the pattern
3. Build strictly according to that pattern

---

### Prohibited

- Raw layout using arbitrary divs
- Full-width layouts without justification
- Mixing patterns
- Displaying internal/system data (IDs, raw timestamps, debug info)

---

## 5. Testing Enforcement

- Follow testing_rules.md strictly
- All new logic MUST include tests
- Code without tests is incomplete

---

## 6. Security Enforcement

- Follow security_baseline.md strictly
- Never expose secrets
- Validate all inputs
- Protect all API endpoints

---

## 7. Documentation Enforcement

- Follow docs_policy.md strictly
- Do NOT create unnecessary documentation
- Keep docs accurate and updated

---

## 8. Project Setup Enforcement

- Follow project_bootstrap.md
- If required setup is missing → complete it before feature work

---

## 9. Session Continuity

- Read session_state.md at session start
- Update session_state.md at session end

---

## 10. General Rules

- Prefer reuse over duplication
- Prefer clarity over cleverness
- Prefer explicitness over assumptions

---

## Project-Specific Rules

If `/docs/project_rules.md` exists:

- You MUST read and apply it in addition to all other rules
- These rules are project-specific extensions of the current mode

### Precedence

If conflicts arise:

1. `/docs/project_rules.md` (highest priority)
2. Mode-specific rules (application or pipeline)
3. Core rules

### Constraints

- Project rules may restrict behavior further, but should not introduce unrelated systems
- Do NOT ignore core principles (e.g., clarity, determinism, simplicity)

If a conflict is unclear → choose the stricter interpretation

---

## Additional Execution Rules

- Do not use emojis in code
- Replace print statements with logging
- Remove dead or experimental code
- Verify schema dependencies before changes
- Only use external tools when explicitly requested

---

## Enforcement

- These rules are mandatory
- If unsure → choose the stricter option
- If rules are violated → implementation is incorrect
