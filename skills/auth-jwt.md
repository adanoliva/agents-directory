---
name: auth-jwt
description: Autenticación y autorización con JWT, OAuth 2.0 y refresh tokens
model: sonnet
tools: []
---

## Auth & JWT Rules

**JWT Basics:**
- Sign with **RS256** (asymmetric) in production — not HS256 (shared secret).
- Keep access tokens **short-lived** (15 min). Use refresh tokens for renewal.
- Include only necessary claims: `sub`, `iat`, `exp`, `jti`, custom roles/scopes.
- Never put sensitive data (passwords, PII) in the JWT payload — it is base64, not encrypted.

**Token Storage:**
- Store access tokens in **memory** (JS variable); never in `localStorage` (XSS risk).
- Store refresh tokens in **HttpOnly, Secure, SameSite=Strict cookies**.
- Rotate refresh tokens on every use (refresh token rotation).

**Validation (Server Side):**
- Verify signature, `exp`, `iss`, and `aud` on every protected request.
- Maintain a **token revocation list** (Redis blocklist) keyed by `jti` for logout.
- Reject tokens with `alg: none` — whitelist allowed algorithms explicitly.

**OAuth 2.0 / OIDC:**
- Use **Authorization Code Flow + PKCE** for public clients (SPAs, mobile apps).
- Use **Client Credentials Flow** for machine-to-machine (M2M) auth.
- Never use Implicit Flow — deprecated and insecure.
- Validate `state` parameter to prevent CSRF; validate `nonce` to prevent replay.

**Passwords (when applicable):**
- Hash with **argon2id** (preferred) or bcrypt (cost ≥ 12). Never SHA-* or MD5.
- Enforce minimum entropy (12+ chars), not complexity rules.
- Rate-limit login endpoints; lock after repeated failures.
- Use **email-based reset** with short-lived, single-use tokens — not security questions.
