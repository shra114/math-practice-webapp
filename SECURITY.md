# Security Policy

## Supported Versions
This project is currently a single-page static web app. Security fixes are applied to the latest code in the default branch.

## Reporting a Vulnerability
If you discover a security issue, please report it responsibly by opening a private security advisory (if enabled) or by contacting the maintainer directly.

Please include:
- A clear description of the issue
- Steps to reproduce
- Potential impact
- Suggested remediation (if available)

## Security Model
This app is low-risk by design:
- Fully client-side (no backend services)
- No authentication or session handling
- No database or server-side storage
- No external third-party JavaScript dependencies

## Current Protections
- User input is displayed using safe text rendering (`textContent`)
- No direct HTML injection from user input
- Wrong-answer export (`review.txt`) is generated locally in-browser via Blob download

## Deployment Recommendations
If hosting publicly (for example on GitHub Pages, Netlify, Vercel), use:
- HTTPS only
- Security headers, especially:
  - `Content-Security-Policy`
  - `X-Content-Type-Options: nosniff`
  - `Referrer-Policy: no-referrer-when-downgrade` (or stricter)
  - `X-Frame-Options: DENY` (or equivalent CSP `frame-ancestors`)

Suggested baseline CSP:

```text
Content-Security-Policy: default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'; img-src 'self' data:; object-src 'none'; base-uri 'self'; frame-ancestors 'none';
```

Note: Inline styles are currently used in `index.html`, so `'unsafe-inline'` is included for `style-src`.

## Out of Scope
The following are currently out of scope unless architecture changes:
- Server-side attacks (no server exists in this project)
- Credential theft (app does not manage credentials)
- Data-at-rest breaches (no persistent backend data store)
