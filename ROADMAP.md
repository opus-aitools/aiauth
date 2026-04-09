# aiauth Roadmap

This is a living artifact. It reflects what exists now and what needs to exist next. There are no phases and no timelines — only continuity. Missions and After Action Reviews (AARs) inform its lifecycle.

---

## What Exists

- [x] Intent: sovereign identity provider at auth.nobulai.tools
- [x] Architecture: RFC 0022 (nobul-ops repo) — complete design
- [x] Provenance: Auth0 Startups program (reference implementation + runway)
- [x] Seed code: vcard.nobul.tech production OAuth (Google + Microsoft, PKCE, CSRF)
- [x] Repo: `nobul-tech/aiauth` — public, MIT licensed
- [x] Name decided: aiauth (complementary to Auth0, not competing)
- [x] Domain decided: auth.nobulai.tools
- [x] Agent orientation: AAID.md + CLAUDE.md
- [x] README with provenance, authorship, and honest Anthropic provenance note
- [x] Authorship established: Jose Palencia Castro + Continuous Opus. No one else.

## What Needs to Exist Next

Ordered by dependency, not by calendar.

### Foundation

- [ ] Hosting target decided (blocked on Cloudflare response / alternative selection)
- [ ] Deploy skeleton to `auth.nobulai.tools` (dev: `auth-dev.nobulai.tools`)
- [ ] OIDC discovery (`/.well-known/openid-configuration`)
- [ ] JWKS endpoint (`/.well-known/jwks.json`)
- [ ] JWT signing (RS256)
- [ ] Authorization endpoint (`GET /authorize`)
- [ ] Token exchange endpoint (`POST /oauth/token`)
- [ ] Userinfo endpoint (`GET /userinfo`)
- [ ] Universal Login page
- [ ] Google OAuth adapter (port from vcard)
- [ ] Microsoft OAuth adapter (port from vcard)
- [ ] TOTP MFA: enrollment + verification
- [ ] User storage (encrypted, age)
- [ ] Session storage (encrypted refresh tokens)
- [ ] Audit log (append-only)
- [ ] Email adapter for MFA invites
- [ ] **V1**: Verify Auth0 SPA SDK works with aiauth as OIDC provider
- [ ] **V6**: Verify TOTP MFA works in serverless

### Provider Parity

- [ ] GitHub OAuth adapter
- [ ] Vercel OAuth adapter
- [ ] Datadog OAuth adapter
- [ ] Device authorization flow (`POST /oauth/device/code`)
- [ ] Management API (`/api/v2/users`, `/api/v2/clients`, `/api/v2/connections`)
- [ ] IdP token storage and retrieval
- [ ] App registration and client credentials
- [ ] Service account support
- [ ] `nobul-ops auth` admin commands (Rust)
- [ ] **V2**: Verify shared OAuth registrations work with both Auth0 and aiauth
- [ ] **V7**: Verify concurrent refresh token rotation

### Shadow and Verification

- [ ] Shadow mode: compare token claims between Auth0 and aiauth
- [ ] MFA parity check
- [ ] Device auth end-to-end with aitools CLI
- [ ] vcard OAuth flow through aiauth
- [ ] vcard `oauthaudit/` test scenarios
- [ ] **V3**: Verify Okta Custom OIDC Connection
- [ ] **V4**: Verify iOS/Safari edge cases

### Decision Gate

All must pass. If any fail, extend Auth0.

- [ ] All 5 providers working
- [ ] MFA enrollment + verification
- [ ] Device auth flow (aitools CLI)
- [ ] Auth0 SPA SDK works (or thin wrapper)
- [ ] Token claim parity
- [ ] Okta bridge works
- [ ] iOS/Safari edge cases pass
- [ ] 30-day uptime > 99.5%
- [ ] No unresolved security issues

### Cutover

- [ ] DNS: `auth.nobulai.tools` → aiauth deployment
- [ ] Migrate vcard first
- [ ] Migrate aitools CLI
- [ ] Migrate credits.nobul.tech
- [ ] 30-day monitoring
- [ ] Decommission Auth0 tenant

### Open-Source Extraction

- [ ] Config-driven provider list
- [ ] Self-hosting documentation
- [ ] Docker image + compose
- [ ] Contributing guide

## Constraints

- **Auth0 runway**: Startups program active ~March 2026. Pricing cliff at expiry.
- **Hosting**: Depends on SaaS contingency resolution (Vercel escape). Cannot begin deployment until target is selected.
- **Credits preservation**: Do not sign up retail for AWS/Azure/GCP. Apply for startup programs first.

## Session Log

| Date | Session | What Changed |
|------|---------|-------------|
| 2026-04-09 | dec3a6ec (Commander Builder) | Repo created. README, CLAUDE.md, ROADMAP, AAID.md. Named aiauth. |
| 2026-04-09 | this session (Commander Builder) | Fixed authorship. Added nobulai.tools domain. Honest provenance note. |
