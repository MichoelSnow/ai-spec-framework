# security_reference.md

## Optional security considerations

This file provides optional context for security-sensitive work. Applicable project requirements and task-specific security procedures remain authoritative.

## When to consult this reference

Use this reference when work affects security-sensitive areas such as:

- authentication or authorization;
- public endpoints;
- external or source ingestion;
- rendering or user-controlled content;
- serialization or deserialization;
- redirects;
- secrets or credentials;
- dependencies;
- other workflows where malformed or hostile input could cross a trust boundary.

Applicable scoped security requirements remain authoritative.

## Vulnerability classes to watch

- Injection risks (SQL, command, template)
- Cross-site scripting (XSS)
- Cross-site request forgery (CSRF)
- Insecure direct object reference (IDOR)
- Open redirects
- Insecure deserialization

## Additional hardening ideas

- Strict CSP and browser security headers can strengthen browser-facing systems.
- Rate limiting can help protect public endpoints.
- Least-privilege network controls can reduce the impact of a compromised component.
- Managed secret stores may be appropriate when available.
- Automated dependency and vulnerability scanning can provide useful ongoing signals.

## Security testing depth

Depending on the project and applicable requirements, consider:
- authn/authz abuse cases
- malformed payload and boundary fuzzing
- failure-mode behavior under degraded dependencies
