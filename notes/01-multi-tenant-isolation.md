# Multi-tenant isolation

**Risk:** one customer reads or changes another customer's data. In a SaaS this is the most damaging bug class.

## How it goes wrong
- The tenant id is taken from the request (a header, query parameter or body field), so a user can send someone else's.
- A query fetches by record id only: `get(invoice_id)` instead of `get(invoice_id, tenant_id)`.
- Background jobs, exports and search indexes forget the tenant filter.
- Caches keyed by record id, not by tenant and id.

## Fixes
1. **Derive the tenant from the verified token only,** never from client input.
2. **Scope every query** by tenant in one shared data-access layer, so a developer cannot forget.
3. **Return 404, not 403,** for another tenant's record. A 403 confirms the record exists.
4. **Add database-level backup:** row-level security (for example PostgreSQL policies) so a missed filter fails closed.
5. **Include the tenant in cache keys, file paths and job payloads.**
6. **Test it:** for every endpoint, create two tenants and assert tenant B cannot read, update or delete tenant A's data.

See a working example: [fastapi-multitenant-starter](https://github.com/Momen-Shili/fastapi-multitenant-starter).
