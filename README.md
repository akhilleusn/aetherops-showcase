# AetherOps

> AI-powered backend incident investigation platform — evidence-first analysis, honest unknowns, safe runbooks.

![Tests](https://img.shields.io/badge/tests-247%20passing-brightgreen)
![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4-green)
![License](https://img.shields.io/badge/license-MIT-blue)

## What is AetherOps?

AetherOps turns backend failures into evidence-backed AI investigations. Unlike tools that give confident-sounding answers without proof, AetherOps only says what the evidence supports — and explicitly tells you what it cannot determine.

**Every AI claim references a specific log evidence ID. No hallucinations passed through silently.**

## Features

- **Evidence-cited AI analysis** — every claim references a log evidence ID
- **Honest unknowns** — confidence capped at 65% for log-only analysis
- **Safe runbooks** — read-only steps only, no destructive suggestions
- **Postmortem drafts** — generated automatically from evidence
- **JWT authentication** — BCrypt passwords, SHA-256 API key hashing
- **2FA / TOTP** — QR setup, backup codes, AES-256-GCM encrypted secrets
- **Google OAuth login** — account linking and 2FA support
- **Account lockout** — 5 failed attempts, 15 minute auto-unlock
- **Password reset** — via email using Resend API
- **Rate limiting** — 100 req/min per API key with response headers
- **Slack alerting** — HIGH and CRITICAL incidents notify your team instantly
- **Multi-tenant isolation** — every query scoped, cross-tenant access impossible
- **Secret masking** — JWT tokens, passwords, API keys redacted before storage and AI
- **Audit logs** — every AI operation logged permanently
- **CORS + Security headers** — production-ready security configuration

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Java 17, Spring Boot 3.4 |
| Database | PostgreSQL 16, Flyway migrations |
| Security | Spring Security, JJWT, BCrypt |
| AI | Anthropic Claude API |
| Infrastructure | Docker, Docker Compose |
| Testing | JUnit 5, MockMvc, H2 |
| Deployment | Railway |

## Quick Start

```bash
git clone https://github.com/akhilleusn/aetherops.git
cd aetherops
cp .env.example .env
docker compose up -d
```

Visit `http://localhost:8080/landing.html`

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| JWT_SECRET | Yes | Min 32 chars |
| ANTHROPIC_API_KEY | No | Falls back to mock AI |
| SLACK_WEBHOOK_URL | No | Slack incident alerts |
| RESEND_API_KEY | No | Password reset emails |
| GOOGLE_CLIENT_ID | No | Google OAuth login |
| TOTP_ENCRYPTION_KEY | No | 2FA secret encryption |

## Testing

```bash
mvn test
# 247 tests, 0 failures
```

## Security Features

- JWT authentication with 24h expiry
- BCrypt password hashing (never plain text)
- SHA-256 API key hashing (raw keys never stored)
- Secret masking before storage and AI processing
- Tenant isolation on every database query
- Rate limiting 100 req/min per API key
- Account lockout after 5 failed attempts
- TOTP 2FA with AES-256-GCM encrypted secrets
- CORS configuration for Railway deployment
- Security response headers (X-Frame-Options, X-XSS-Protection, etc.)

## License

MIT License — see [LICENSE](LICENSE) for details.

---

Built with Java 17 · Spring Boot 3.4 · PostgreSQL · Docker
