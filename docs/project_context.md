# Project Context

This document records project facts and accepted decisions that materially affect sensible solutions. It is project context, not a generic rules file.

Defaults are assumed in the absence of contrary project information. They are not binding requirements and may be overridden without violating the framework.

## Default assumptions

- The project is primarily maintained by one developer.
- Simplicity and a low maintenance burden are preferred.
- Large-team processes and enterprise organizational needs are not assumed.
- Backward compatibility is not required unless there are real consumers, persisted data, or an explicit commitment.
- Existing project tooling and infrastructure are preferred over introducing new systems.
- Speculative future scale does not drive design decisions.
- Verification is proportional to risk and cost.
- Security controls match actual exposure and data sensitivity.
- Expensive compute, API, or runtime work starts with the narrowest useful check.
- Documentation remains minimal and authoritative rather than exhaustive.

## Project-specific overrides and additions

Record only facts, accepted decisions, or deviations from the defaults that materially affect the project.

- Maintainer(s) and ownership model:
- Users and audience:
- Project maturity and stability expectations:
- Deployment environments and exposure:
- External consumers and published interfaces:
- Persistent data that must be preserved:
- Compatibility commitments and supported platforms/runtimes:
- Security and privacy requirements:
- Operational, runtime, performance, and cost constraints:
- Architecture and technology decisions:
- Other deviations from defaults:
