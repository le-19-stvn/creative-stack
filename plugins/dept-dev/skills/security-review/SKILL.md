---
name: security-review
description: End-of-development defensive hardening audit for a web project — scored, with fixes. Runs a defensive configuration checklist (security headers, CORS, TLS, file exposure, form protection, cache/SRI/security.txt), scores the result out of 100 by severity, and proposes config diffs to apply after human review. Use when hardening before launch, or when the user asks "is this secure to ship", "security audit", "hardening review", "check the headers/CORS/TLS". This is a NON-INTRUSIVE configuration review, not a penetration test.
---

# Security Review (defensive hardening audit)

A last-mile hardening pass over the project's **code and configuration**. It reads and reasons; it never attacks. Read `STACK.md` and `CLAUDE.md` first for deployment context (hosting, framework, where headers are set). (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)

## STRICT LIMITS — read before running

- This is a **DEFENSIVE CONFIGURATION REVIEW, NOT a penetration test.** Never attempt to exploit, inject, fuzz, brute-force, or bypass anything. No live probing of third-party or production systems.
- You only **read** source and config and **propose** changes. You do not perform offensive actions.
- **Mandatory disclaimer** — include this verbatim in every report you produce:

  > **Ceci est une revue de bonnes pratiques automatisée, non-intrusive. Ne remplace pas un audit de sécurité professionnel / test d'intrusion réglementé.**

## Delegate first (portable)

If a `security-reviewer` agent is available in the install, hand the code to it for vulnerability-level review and fold its findings into this report. If it's absent, the checklist below stands on its own. **The scored report is always produced by this skill** — delegation only enriches it.

## The checklist

Inspect config files (e.g. `vercel.json`, `netlify.toml`, nginx/Caddy config, middleware, framework headers) and relevant code. For each item: present, misconfigured, or missing.

- **Security headers**
  - `Content-Security-Policy` — present? **Flag `unsafe-inline` / `unsafe-eval`** in script-src.
  - `Strict-Transport-Security` — present? includeSubDomains? **preload?**
  - `X-Frame-Options` (or CSP `frame-ancestors`), `X-Content-Type-Options: nosniff`, `Referrer-Policy`, `Permissions-Policy`.
- **CORS** — **flag `Access-Control-Allow-Origin: *`** (wildcard), especially with credentials. Recommend an explicit allowlist.
- **TLS** — obsolete protocols (TLS < 1.2), and missing HTTP→HTTPS redirect.
- **Exposure** — reachable `.git/`, `.env`, backups (`.bak`, `~`, `.old`), source maps in prod, other sensitive files; infra metadata leaked in headers (`Server`, `X-Powered-By`, version banners).
- **Forms** — submission endpoints with no anti-abuse (honeypot / captcha / rate-limit).
- **Cache** — sensitive responses without `Cache-Control: no-store`; overly permissive caching of authenticated content.
- **SRI** — third-party `<script>`/`<link>` from a CDN without `integrity`.
- **security.txt** — present at `/.well-known/security.txt`?

## Scoring (indicative, out of 100)

Start at **100**, deduct per finding by severity, add bonus for strong practices already in place, then clamp to **[0, 100]** (the floor).

| Severity | Deduction | Typical |
|---|---|---|
| **Critique** | −20 | wildcard CORS with credentials, `.env`/`.git` exposed, no TLS |
| **Haute** | −8 | no CSP, no HSTS, `unsafe-inline` script-src |
| **Moyenne** | −4 | missing `X-Content-Type-Options`/`Referrer-Policy`/`Permissions-Policy`, no HTTP→HTTPS redirect |
| **Basse** | −1 | missing `security.txt`, verbose `Server` header |
| **Bonus** | +1 to +2 each | strong practices already present (nonce-based CSP, HSTS preload, SRI everywhere) |

Label the score as indicative, never as a certification. Give each finding an **estimated effort** (e.g. *trivial — one config line*, *low*, *medium — needs infra change*).

## Report format

Deliver a clear report (and save to `SECURITY-REVIEW.md` at project root if the user wants a record). Structure:

1. **Disclaimer** (verbatim, above) and the indicative **score /100** with the tally that produced it.
2. **Findings**, ordered by severity. Each: **Finding → Risk → Recommendation**, with severity and estimated effort.
3. **Already in place** — the strong practices you found, so the report credits real work, not just gaps.

## Fixes

For **configuration** fixes (headers in `vercel.json`, CORS allowlist, redirect rules, cache directives, adding `security.txt`/SRI): **propose the diff, explain it, and apply only after the human approves.** Never silently rewrite security config. For code-level issues (form anti-abuse, exposed routes), describe the change and let the human or `feature-build` implement it.

## Before calling it done

The disclaimer is present, every finding has risk + recommendation + effort, the score's math is shown, and no offensive action was taken. If you strayed into probing or exploitation, you've broken the skill's contract — stop and report only what you read.
