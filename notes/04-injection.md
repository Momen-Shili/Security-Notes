# Injection

**Risk:** untrusted input is interpreted as code or a command (SQL, OS command, template, LDAP, NoSQL).

## Rules
- **SQL:** use parameterized queries or an ORM's bound parameters. Never build SQL with string concatenation or f-strings. Identifiers (table or column names) cannot be parameterized, so allow-list them.
- **OS commands:** avoid them. If unavoidable, pass an argument list without a shell, and validate input against an allow-list.
- **Templates:** never render user input as a template; escape output by default.
- **XSS:** output-encode for the context (HTML, attribute, JavaScript, URL), set a Content-Security-Policy, and sanitize any HTML you must accept with a maintained library.
- **Deserialization:** do not deserialize untrusted data with formats that can run code (for example Python pickle).
- **SSRF:** when the server fetches a user-supplied URL, allow-list hosts, block private and link-local address ranges, and re-check after redirects.

## Mindset
Validate on input, encode on output, and give the database account only the privileges the application needs, so one bug cannot drop everything.
