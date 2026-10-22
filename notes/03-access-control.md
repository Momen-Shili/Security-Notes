# Access control

**Risk:** users do things they should not (IDOR, privilege escalation). It is the most common serious web bug.

## IDOR (insecure direct object reference)
A user changes `/invoices/41` to `/invoices/42` and sees someone else's invoice, because the server checked that the user is logged in but not that the invoice is theirs.

**Fix:** authorize every object access: "may this user do this action on this record?" Do not rely on hidden ids or UI buttons.

## RBAC rules that hold up
- Deny by default; grant explicitly.
- Check permissions on the server for every request, including internal APIs and exports.
- Centralize checks in one policy layer instead of scattering `if role == ...`.
- Re-check on writes: a user who may read a record may not be allowed to edit it.
- Sensitive actions (delete, export, change role, payments) need their own permission and an audit log entry.
- Never let a user assign themselves a higher role: validate the role field on user updates ("mass assignment").

## Test
For each role, list what it must NOT do and write a test that tries it.
