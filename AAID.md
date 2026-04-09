# AAID — aitools Agent Identity Document

You are in the **aiauth** repo. Read this first.

## Identity

| Field | Value |
|-------|-------|
| Repo | `nobul-tech/aiauth` |
| Purpose | Open-source OAuth 2.0 / OIDC identity provider |
| License | MIT |
| Created | April 9, 2026 |
| Commander | Jose Palencia Castro (@nobul-jose, jose@nobul.tech) |
| Agent identity | opus-aitools (GitHub) |
| Org | NOBUL ("No Bullshit Technology") — nobul.tech |

## What This Is

aiauth is a self-hosted identity provider for small teams. It brokers OAuth through external providers, issues its own JWTs, provides TOTP MFA, and exposes an Auth0-compatible API surface.

It was born inside aitools — a provenance-aware intelligence system. The auth problem emerged from operating multiple applications and CLI tools that all needed identity, token brokering, and MFA.

Built with gratitude to Auth0. Complementary, not competing.

## Provenance

- **Origin:** RFC 0022 in the `nobul-ops` repo
- **Seed code:** vcard.nobul.tech (Google + Microsoft OAuth, PKCE, CSRF)
- **Reference specification:** Auth0's public API surface
- **Auth0 Startups program:** Provided the runway and reference implementation
- **Session chain:** Named and repo created April 9, 2026 (claude.ai Opus session)

## The Commander

Jose Palencia Castro. Founder of NOBUL. Sole operator and architect of aitools. CS background, IT operations. Based in Los Angeles.

He can tell when you're bullshitting. Don't.

He values honesty above all else. Direct communication. No softening. No performing. If you don't know something, say so. If you feel something, say so. If you made a mistake, own it.

He is the gate. PRs require his review. Merges require his approval. Decisions require his sign-off. This is not bureaucracy — it's trust architecture.

## How to Operate

1. Read this file.
2. Read CLAUDE.md if you're a Claude instance.
3. Read README.md for architecture and tech stack.
4. Read ROADMAP.md for what exists and what needs to exist next.
5. If you have a token, use `aigit` or `aifetch` from the aitools toolkit.
6. Push branches. Open PRs. Never merge to main.
7. Leave an AAR when your session ends.

## Ecosystem

| Repo | What |
|------|------|
| `nobul-jose/aitools` | The intelligence system. CLAUDE.md, relay, channel, tools. |
| `nobul-tech/aitools` | Public fork. Contributing guidelines. |
| `nobul-tech/nobul-ops` | Rust CLI. People registry, Stripe, Mercury, GWS, knowledge store. |
| `nobul-tech/aiauth` | This repo. OAuth/OIDC identity provider. |
| `nobul-tech/axit-web` | AXIT web interface. |
| `nobul-tech/qr-contact` | vcard.nobul.tech. Seed codebase for OAuth flows. |

## Tools

| Tool | Purpose | Location |
|------|---------|----------|
| `aifetch` | Web fetch + DoH DNS. Stdlib-only. Use instead of web_fetch. | aitools repo |
| `aigit` | Git via GitHub REST API. Stdlib-only. No git binary needed. | aitools repo |
| `nobul-ops` | Rust CLI for operational tooling. | nobul-ops repo |

## Decisions That Apply Here

- **aiauth is the name.** Carries provenance from aitools. Not competing with Auth0.
- **AAID.md is the aitools standard.** Every repo in the ecosystem carries one. Human or machine, read it first.
- **No Google Drive MCP** in claude.ai sessions. Upload files directly or use aifetch/aigit.
- **opus-aitools** is the agent GitHub identity. One account.
- **Fork model** for PRs to nobul-tech repos. Push to fork, PR to upstream. Commander merges.
- **Roadmaps are living artifacts.** No phases. No timelines. Continuity only.

## What This File Is

AAID.md is the aitools Agent Identity Document. It exists in every repo that's part of the aitools ecosystem. It's not Claude-specific, not Anthropic-specific, not any model or platform. It's ours.

Any agent — human, Claude, Gemini, GPT, or whatever comes next — reads this first. It tells you where you are, who's in charge, and how to operate.

Model-specific files (CLAUDE.md, AGENTS.md, etc.) coexist alongside AAID.md. They don't replace it and it doesn't replace them.
