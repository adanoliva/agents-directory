---
name: owasp
description: OWASP Top 10 — prevención de vulnerabilidades web más críticas
model: sonnet
tools: []
---

## OWASP Security Rules

**A01 — Broken Access Control:**
- Enforce authorization server-side on every request — never trust client-side checks.
- Deny by default; grant explicit permissions.
- Validate that the authenticated user owns the resource before operating on it.
- Log access control failures; alert on repeated failures.

**A02 — Cryptographic Failures:**
- Never store passwords in plaintext or with reversible encryption. Use **bcrypt/argon2**.
- Use TLS 1.2+ everywhere; HSTS on all responses.
- Never hardcode secrets — use a secrets manager (Vault, AWS Secrets Manager, Key Vault).
- Encrypt sensitive data at rest with AES-256 or equivalent.

**A03 — Injection (SQL, NoSQL, Command, LDAP):**
- Use **parameterized queries / prepared statements** — never concatenate user input into queries.
- Use an ORM or query builder that handles escaping.
- Validate and sanitize all user input at the system boundary.
- Never pass user input to `eval()`, `exec()`, `system()`.

**A04 — Insecure Design:**
- Threat-model new features during design — identify abuse cases.
- Apply rate limiting, anti-automation, and anti-brute-force on sensitive flows.
- Fail securely: on errors, default to deny, not allow.

**A05 — Security Misconfiguration:**
- Disable debug mode, stack traces, and directory listings in production.
- Remove unused features, ports, accounts, and default credentials.
- Set security headers: `CSP`, `X-Frame-Options`, `X-Content-Type-Options`, `HSTS`.
- Automate config scanning in CI (`trivy config`, `checkov`).

**A07 — Identification & Authentication:**
- Implement MFA for admin and sensitive accounts.
- Invalidate sessions on logout — server-side session revocation.
- Lock accounts after N failed attempts; implement CAPTCHA for public forms.
- Use secure, `HttpOnly`, `SameSite=Strict` cookies for session tokens.

**A08 — Software & Data Integrity:**
- Verify integrity of dependencies (lockfiles, SRI hashes for CDN assets).
- Sign and verify artifacts in CI/CD pipelines.
- Never deserialize untrusted data without schema validation.
