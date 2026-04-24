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

- If framework audit = FAIL → stop
- Do not run engineering review until audit passes
- Exploratory review is non-blocking