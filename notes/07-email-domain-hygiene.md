# Email and domain hygiene

**Risk:** anyone can send email that appears to come from your domain (phishing), and your real mail lands in spam.

## The three records
- **SPF:** lists the servers allowed to send for your domain. End with `-all` (or `~all` while testing). Keep to 10 DNS lookups or fewer.
- **DKIM:** signs each message so receivers can check it was not altered and came from you. Use 2048-bit keys where supported.
- **DMARC:** tells receivers what to do when SPF and DKIM fail and where to send reports. Roll out in stages: `p=none` with reporting, then `p=quarantine`, then `p=reject`.

## Also
- Serve HTTPS everywhere with HSTS once you are sure every subdomain supports it.
- Add security headers: `Content-Security-Policy`, `X-Content-Type-Options`, `Referrer-Policy`, and frame protection.
- Remove dangling DNS records that point to services you no longer use (subdomain takeover).
- Publish a `security.txt` so researchers know how to reach you.

A passive checker for these: [posture-check](https://github.com/Momen-Shili/posture-check) (use it only on domains you own).
