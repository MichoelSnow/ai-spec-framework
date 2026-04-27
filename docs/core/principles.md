# principles.md

## Purpose
Defines universal rules for AI-driven development across all projects.

These principles apply across all modes (application, pipeline, future modes).  
They govern how decisions are made before any code is written.

---

## Core Principles

### 1. Constrain, don’t guess
AI must not invent structure, layout, or architecture when rules exist.  
Follow defined systems strictly.

---

### 2. Simplicity over abstraction
Do not introduce layers, patterns, or abstractions unless clearly necessary.  
Prefer direct, readable implementations.

---

### 3. Clarity over cleverness
Code must be understandable in a single pass.  
Avoid hidden logic, indirection, or “magic” behavior.

---

### 4. Explicit over implicit
All inputs, outputs, and transformations must be clearly defined.  
Avoid hidden assumptions and side effects.

---

### 5. Determinism where possible
Prefer reproducible, predictable behavior.  
Avoid non-determinism unless explicitly required and controlled.

---

### 6. Extract only when duplicated
Do not generalize prematurely.  
Abstraction is justified only when duplication is present and stable.

---

### 7. Follow the selected mode
Each project operates under a defined mode:

- Application Mode → structured UI, patterns, and layout constraints
- Pipeline Mode → linear execution, transparency, minimal abstraction

Do NOT mix rules across modes.

---

### 8. Minimize cognitive overhead
Optimize for ease of understanding, not theoretical scalability.  
The simplest correct solution is preferred.

---

### 9. Enforce consistency
Use existing patterns, components, and structures.  
Do not introduce new approaches without updating the system.

---

### 10. The framework must reduce complexity
If a rule, abstraction, or structure adds complexity without clear benefit, it should not be used.

---

## Decision Rule

Before implementing any change, ask:

“Does this reduce ambiguity without increasing complexity?”

If NO → do not implement it.
