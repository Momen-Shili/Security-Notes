# File uploads

**Risk:** malware storage, stored XSS through SVG or HTML, path traversal, denial of service, or code execution.

## Checklist
- Allow-list extensions and check the real content type; do not trust the client's `Content-Type` or filename.
- Set a maximum size (and limit the request body at the proxy too).
- **Rename files** to a random id; never use the user's filename in a path.
- Store outside the web root, or in object storage, and serve through a controlled endpoint.
- Serve user files with `Content-Disposition: attachment` and `X-Content-Type-Options: nosniff`, ideally from a separate domain.
- Treat SVG and HTML as active content: sanitize or disallow.
- Scan with antivirus if files are shared between users.
- Strip image metadata (EXIF) if location privacy matters.
- Scope paths and download authorization by tenant (see note 01).
