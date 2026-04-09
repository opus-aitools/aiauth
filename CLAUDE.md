# CLAUDE.md — Claude-Specific Orientation for aiauth

Read AAID.md first. This file is for Claude instances only.

## Identity

- **Repo**: `nobul-tech/aiauth`
- **License**: MIT
- **Language**: TypeScript (server), Rust (admin CLI via nobul-ops), Vanilla JS (Universal Login)
- **Created**: April 9, 2026
- **Commander**: Jose Palencia Castro (@nobul-jose, jose@nobul.tech)
- **Domain**: auth.nobulai.tools

## What This Is

A self-hosted identity provider that:
1. Brokers OAuth through external providers (Google, Microsoft, GitHub, Vercel, Datadog)
2. Issues its own JWTs (access, refresh, ID tokens)
3. Provides TOTP MFA for all human users
4. Exposes an Auth0-compatible API surface so existing apps can switch with a config change
5. Stores and retrieves upstream IdP tokens for CLI tooling (the token brokering pattern)

Deployed at `auth.nobulai.tools`. Self-hosters use their own domain.

## What This Is Not

- Not a fork of Auth0, Keycloak, Authentik, or Zitadel
- Not competing with Auth0 — complementary to it
- Not enterprise IdP software — purpose-built for small teams (1–25 users)
- Not authored by Anthropic — authored by Jose and Continuous Opus

## Key Design Decisions

1. **Auth0 compatibility.** Switching is `AUTH_DOMAIN=auth.nobulai.tools` — one env var.
2. **TOTP MFA from day 1.** No proprietary authenticator. Any RFC 6238 app works.
3. **Provider adapter pattern.** Each OAuth provider is a module. App code never touches provider APIs directly.
4. **Encrypted storage.** IdP tokens, MFA secrets, and refresh tokens encrypted at rest using age (AES-256-GCM).
5. **Five identity types.** People, apps, service accounts, devices, CI/CD runners.
6. **Database portable.** Adapter interface — SQLite, Postgres, Turso, Cloudflare D1.
7. **Open-source from birth.** MIT license. Configuration-driven. No hardcoded assumptions.

## Relationship to Other Repos

| Repo | Relationship |
|------|-------------|
| `nobul-ops` | Admin CLI (`nobul-ops auth` commands). RFC 0022 lives here. |
| `aitools` | Primary consumer — `aitools auth login` uses device auth flow + token brokering |
| `qr-contact` (vcard) | Seed codebase for Google/Microsoft OAuth. First app to migrate. |
| `nobul-aws-credits` (credits) | Second app to migrate. |

## Verification Blockers

| ID | Claim | Blocker? |
|----|-------|----------|
| V1 | Auth0 SPA SDK works with any OIDC provider | **Yes** — determines flip mechanism |
| V2 | OAuth providers allow dual redirect URIs | Yes |
| V6 | TOTP MFA works in serverless | Yes |
| V7 | Refresh token rotation has no race conditions | Yes |

## Conventions

- No custom cryptography. Standard libraries only (`jose`, `otpauth`, `age`).
- Every endpoint maps to a documented Auth0 equivalent.
- Tests verify parity with Auth0 token claims.
- Adapter interfaces for everything that could be swapped: providers, storage, email, hosting.

## For the Agent

Read AAID.md first. If you need the full RFC, ask the Commander to upload `0022-aiauth_draft.md` from nobul-ops.

Don't perform. Don't soften. Build.
