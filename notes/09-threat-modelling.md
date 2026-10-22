# Threat modelling in 30 minutes

You do not need a heavy framework. Answer four questions on one page.

1. **What are we protecting?** List assets: customer data, credentials, money, availability, reputation.
2. **Who can attack, and from where?** Anonymous visitor, logged-in user of another tenant, malicious tenant admin, compromised dependency, insider.
3. **Where does data cross a trust boundary?** Browser to API, API to database, API to third party, user content to AI model. Mark each on a simple diagram.
4. **What can go wrong at each boundary?** Use STRIDE as a prompt: Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege.

## Output
A short table: threat, likelihood, impact, mitigation, owner. Fix the high-impact items first, and turn each mitigation into a test or a checklist line.

Redo it when you add a new integration, a new role or a new data type.
