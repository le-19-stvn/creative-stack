---
name: content-strategy
description: Force a decided editorial strategy instead of publishing whatever fills the calendar, and write it to CONTENT-STRATEGY.md. Use before producing any content, or when the user asks "what should we publish", "content plan", "editorial calendar", "what topics". This is the content department's anti-slop core — the CONTENT-STRATEGY.md it produces is what content-piece and content-critic hold every piece to.
---

# Content Strategy

Decide what this brand publishes and why — before a single piece is written. Produce a `CONTENT-STRATEGY.md` that commits to an editorial point of view instead of chasing volume.

Read `TASTE.md`, `POSITIONING.md`, and `BRAND.md` first if they exist. This doc **references** them — it does not redefine positioning or voice. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)

## What CONTENT-STRATEGY.md decides (and ONLY this)

Keep it to these four. Positioning lives in `POSITIONING.md`, voice lives in `BRAND.md`; link, don't copy.

- **Editorial pillars** — the 3–5 themes this brand has authority to own, each traced to a claim in `POSITIONING.md`. Not "topics we could cover" — the themes we choose to be known for.
- **Formats** — the specific shapes we publish (deep-dive essay, teardown, changelog, tutorial, FAQ…) and, just as important, the ones we deliberately don't.
- **Recurring angle** — the consistent lens across pieces: the stance, the enemy, the way this brand sees the subject that others don't. Traced to `POSITIONING.md`/`BRAND.md`.
- **Cadence** — realistic rhythm per format. Sustainable and chosen, not "as much as possible." Under-publishing on-angle beats flooding off-angle.

## Rules

- **Reference, never duplicate.** Positioning and voice are owned elsewhere. If you're rewriting them here, stop and link instead.
- **Pillars earn their place.** Each maps to a positioning claim the brand can actually back. Drop any pillar that's just "a thing people search for."
- **Cadence is a ceiling, not a quota.** It caps commitment; it never obligates filler to hit a number.

## Output

Write `CONTENT-STRATEGY.md` at project root. Short and declarative — read at the start of every content session and by `content-critic` on every piece. Link it from `CLAUDE.md`.

## Before calling it done

Every pillar traces to `POSITIONING.md`, the recurring angle is nameable in one sentence, and nothing here restates voice or positioning. If it reads like a generic content calendar any brand could run, redo it.
