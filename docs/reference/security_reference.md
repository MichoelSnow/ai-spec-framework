# security_reference.md

## Expanded security guidance

This file provides additional context beyond the operating baseline.

## Vulnerability classes to watch

- Injection risks (SQL, command, template)
- Cross-site scripting (XSS)
- Cross-site request forgery (CSRF)
- Insecure direct object reference (IDOR)
- Open redirects
- Insecure deserialization

## Additional hardening ideas

- Use strict CSP and browser security headers.
- Use rate limiting for public endpoints.
- Apply least-privilege network controls.
- Use managed secret stores when available.
- Add automated dependency and vulnerability scanning.

## Security testing depth

Beyond required tests, consider:
- authn/authz abuse cases
- malformed payload and boundary fuzzing
- failure-mode behavior under degraded dependencies
