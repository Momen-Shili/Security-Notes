# Authentication and sessions

**Risk:** account takeover, forged or replayed tokens.

## Checklist
- Hash passwords with a slow algorithm (Argon2id or bcrypt). Never encrypt, never use a fast hash.
- Rate-limit login and password-reset endpoints; lock or slow down after repeated failures.
- Give the same response for "unknown user" and "wrong password".
- Password reset tokens: random, single-use, short expiry, stored hashed.
- **JWT:** verify signature and algorithm explicitly (never accept `none`), check `exp`, `aud` and `iss`, keep access tokens short-lived and rotate refresh tokens.
- Do not put secrets or sensitive data in a JWT: it is signed, not encrypted.
- Cookies: `HttpOnly`, `Secure`, `SameSite=Lax` or `Strict`.
- Offer MFA for admin accounts at least.
- Invalidate sessions on password change and logout.

## Common mistake
Trusting a role or tenant claim the client can influence. Roles belong in the server-side record, or in a token you signed yourself.
