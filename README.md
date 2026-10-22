# security-notes

Practical, defensive security notes from building and reviewing multi-tenant SaaS and AI-agent systems. Each note is short: the risk, how it shows up in real code, and the fix.

> Defensive and educational. No exploit code. Only test systems you own or have written permission to test.

## Notes

| Topic | Note |
|---|---|
| Tenant isolation | [01-multi-tenant-isolation.md](notes/01-multi-tenant-isolation.md) |
| Authentication and sessions | [02-auth-and-sessions.md](notes/02-auth-and-sessions.md) |
| Access control (IDOR, RBAC) | [03-access-control.md](notes/03-access-control.md) |
| Injection (SQL, command, template) | [04-injection.md](notes/04-injection.md) |
| File uploads | [05-file-uploads.md](notes/05-file-uploads.md) |
| Secrets and configuration | [06-secrets-and-config.md](notes/06-secrets-and-config.md) |
| Email and domain hygiene (SPF, DKIM, DMARC) | [07-email-domain-hygiene.md](notes/07-email-domain-hygiene.md) |
| Prompt injection in AI agents | [08-prompt-injection-agents.md](notes/08-prompt-injection-agents.md) |
| Threat modelling in 30 minutes | [09-threat-modelling.md](notes/09-threat-modelling.md) |

Also: [SaaS pre-launch checklist](checklist.md).

## Related repos

[posture-check](https://github.com/Momen-Shili/posture-check) · [fastapi-multitenant-starter](https://github.com/Momen-Shili/fastapi-multitenant-starter) · [agent-injection-tests](https://github.com/Momen-Shili/agent-injection-tests)

## Contact

shili.momen@gmail.com · [Portfolio](https://momenshili.app) · [LinkedIn](https://www.linkedin.com/in/momen-shili-a00291192)

MIT licensed. Corrections welcome through issues.
