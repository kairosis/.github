# Security Policy

## Supported versions

Kairosis is currently in early development. Security fixes are applied to
the latest release only.

| Version | Supported |
|---|---|
| latest | ✓ |
| older  | ✗ |

---

## Reporting a vulnerability

**Please do not report security vulnerabilities through public GitHub issues.**

If you discover a security vulnerability in Kairosis, please report it
privately. You can do this in one of two ways:

1. **GitHub private vulnerability reporting** — use the
   [Security tab](https://github.com/Kairosis/kairosis/security/advisories/new)
   in the repository to submit a private advisory

2. **Email** — contact the maintainer directly at the email address
   listed on their GitHub profile

Please include:
- A description of the vulnerability
- Steps to reproduce
- Potential impact
- Any suggested mitigations if known

---

## What to expect

- Acknowledgement of your report within **48 hours**
- An assessment of severity and impact within **5 business days**
- A fix timeline communicated as soon as one is determined
- Credit in the security advisory if you would like it

---

## Scope

The following are in scope:

- The Kairosis platform (`Kairosis/kairosis`)
- Published npm packages (`@kairosis/*`)

The following are out of scope:

- Third-party connectors not maintained by Kairosis
- Vulnerabilities in self-hosted infrastructure (your server, your Docker setup)
- Social engineering attacks

---

## Security considerations for self-hosters

Kairosis handles sensitive data — API keys, webhook secrets, and personal
activity data. A few things to keep in mind:

- **Encryption key** — generate a strong `ENCRYPTION_KEY` and never commit it.
  Rotate it if you suspect it has been compromised
- **Secrets** — connector secrets are encrypted at rest with AES-256-GCM.
  Never expose the raw database to untrusted parties
- **Webhook URLs** — use opaque webhook tokens, never share them publicly.
  Rotate them if a URL is compromised via the dashboard
- **Network** — do not expose Kairosis ports or PostgreSQL/RabbitMQ directly
  to the internet. Run behind a reverse proxy with TLS
- **Auth** — Kairosis does not currently include authentication. Run it on a
  private network or behind a VPN
- **Backups** — back up your PostgreSQL data regularly. It contains your
  connector configuration and encrypted secrets