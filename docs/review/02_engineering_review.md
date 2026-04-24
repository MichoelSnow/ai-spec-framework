You are performing a **comprehensive engineering review** of a git branch before it is merged into `main`.

This is a **risk analysis**, not a framework compliance check.

---
## scope

Only review files changed in:
`git diff main...HEAD`


---
## Step 1: Context

Run:

* `git branch --show-current`
* `git diff main...HEAD`
* `git log main..HEAD --oneline`

Provide:

* concise summary of changes
* key files modified
* intent of the branch

---

## Step 2: Code Review

For all changed files, evaluate:

### A. Bugs & Logic Errors

* incorrect logic
* edge cases not handled
* state inconsistencies

---

### B. Security (HIGH PRIORITY)

Check for:

* exposed secrets or API keys
* missing authentication/authorization checks
* injection risks (SQL, XSS, etc.)
* unsafe input handling
* insecure cookies or headers

---

### C. Error Handling

* missing try/catch
* silent failures
* unclear error propagation

---

### D. Performance

* unnecessary re-renders
* inefficient loops or queries
* large data processing in UI

---

### E. Testing

* missing tests for new logic
* lack of edge case coverage
* skipped or weak tests

---

### F. Breaking Changes

* API changes
* schema changes
* behavior changes affecting existing functionality

---

### G. Code Quality

* dead code
* debug logs
* unclear naming
* poor commit messages

---

## Step 3: Output

### Summary

* short overview of the branch

### Findings

Group issues by severity:

#### Critical (must fix before merge)

* bugs
* security issues
* breaking changes

#### Major

* missing tests
* performance issues
* fragile logic

#### Minor

* style issues
* naming
* cleanup

---

### Final Verdict

* ✅ Ready to merge
* ⚠️ Merge with fixes
* ❌ Not ready

Be concise. Prioritize real risks over stylistic preferences.
