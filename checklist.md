# SaaS pre-launch security checklist

Tick each item or write down why it does not apply.

## Identity and access
- [ ] Passwords hashed with Argon2id or bcrypt; login and reset rate-limited
- [ ] Tokens verified (signature, algorithm, expiry); sessions invalidated on logout
- [ ] Every endpoint checks authorization on the record, not just login
- [ ] Tenant id comes only from the verified token; cross-tenant access returns 404
- [ ] Cross-tenant tests exist for every endpoint
- [ ] Admin accounts use MFA

## Data
- [ ] Parameterized queries everywhere
- [ ] Database account has least privilege; row-level security considered
- [ ] Backups run and a restore has been tested
- [ ] Sensitive data encrypted in transit (TLS) and at rest where needed
- [ ] Uploads validated, renamed, size-limited and served safely

## Secrets and config
- [ ] No secrets in Git history; secret scanning in CI
- [ ] Production has debug off, no default accounts, no open admin panels
- [ ] Logs contain no tokens or passwords

## Edge
- [ ] HTTPS and HSTS; security headers set
- [ ] SPF, DKIM, DMARC published
- [ ] Rate limits and request size limits
- [ ] Dependencies updated; automated vulnerability alerts on

## Operations
- [ ] Audit log for sensitive actions
- [ ] Monitoring and alerting for errors and failed logins
- [ ] Incident plan: who is called, how to rotate secrets, how to notify customers
- [ ] `security.txt` published

## If the product uses AI agents
- [ ] Tools limited to least privilege; human confirmation for risky actions
- [ ] Indirect prompt-injection tests in CI
