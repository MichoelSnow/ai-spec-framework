# Scoped Requirements

This directory contains binding project or subsystem requirements. A requirement defines correctness only when its stated applicability includes the current work.

Each requirement document should state its applicability near the top, for example:

```text
# Scoring Requirements

Applies when:
- modifying scoring logic
- modifying scoring configuration
- modifying consumers of scoring outputs
```

Keep requirements focused on authoritative behavior for a project or subsystem. Do not add a registry, manifest, schema, or other discovery machinery; inspect the relevant documents directly when the affected subsystem is known.
