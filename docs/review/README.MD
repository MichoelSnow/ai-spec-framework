# review pipeline

This directory defines the required pre-merge review process.

## execution order

1. 01_framework_audit.md
   - strict pass/fail gate
   - blocks merge on violation

2. 02_engineering_review.md
   - identifies bugs, security issues, and risks

3. 03_exploratory_review.md
   - optional insights and improvement suggestions

## rules

- If framework audit = FAIL -> stop
- Do not run engineering review until audit passes
- Exploratory review is non-blocking

## prompts

### Framework Audit Prompt

```text
Run /docs/review/01_framework_audit.md exactly as written.
Audit only changed files from git diff main...HEAD.
Also enforce /docs/project/project_rules.md when present.
Return only:
- Verdict: PASS or FAIL
- Critical Violations
Stop after this audit if verdict is FAIL.
```

### Engineering Review Prompt

```text
Run /docs/review/02_engineering_review.md exactly as written.
Review only changed files from git diff main...HEAD.
Use full repository context to assess impact of changed files.
Account for /docs/project/project_rules.md when present.
Focus on bugs, security risks, missing tests, performance risks, and breaking changes.
Return severity-grouped findings and final merge readiness verdict.
```

### Exploratory Review Prompt

```text
Run /docs/review/03_exploratory_review.md exactly as written.
Review only changed files from git diff main...HEAD.
Use full repository context to assess architecture and maintainability impact.
Account for /docs/project/project_rules.md when present.
Provide high-signal, non-blocking feedback:
- high-level assessment
- soft risks
- thoughtful author questions
- optional improvements
```
