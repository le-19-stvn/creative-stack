---
name: brand-identity
description: Build a brand identity — positioning, personality, palette, typography, logo direction, and tone — bound to the project's declared taste. Use when the user works on a brand, visual identity, style guide, charte graphique, naming, or logo. Trigger on brand, identity, palette, typography, logo, tone of voice. Reads TASTE.md first and produces BRAND.md.
---

# Brand Identity

Produce a brand identity that reflects a human point of view, not a generated default.

## Before anything

Read `TASTE.md`. If it doesn't exist, invoke the core `taste-layer` skill first — no identity work begins without a declared taste. The references and anti-references there govern every choice below. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)

## Build order

Lock each before moving on:

1. **Positioning** — one sentence: what it is, for whom, why it's different.
2. **Personality** — 3-5 adjectives + a "we are / we are not" pair. Pull directly from `TASTE.md`'s feelings.
3. **Palette** — primary, secondary, neutrals, semantic. HEX + usage rules. Contrast ≥ 4.5:1 for text. Tie the accent choice to a reference in `TASTE.md`, not to a trend.
4. **Typography** — a deliberate display/body pairing with a real scale, weights, fallbacks. No default system stack unless that's a stated choice.
5. **Logo direction** — concept, clear space, min size, mono variants, do/don't. (Claude directs and briefs; final mark may be executed in a dedicated tool — see note.)
6. **Tone of voice** — register, sentence length, words to use/avoid, drawn from `TASTE.md`.

Output to `BRAND.md` at project root.

## Note on execution

For the final logo/image render, Claude's job is to **direct**: brief, references, and critique of the rendered options against `TASTE.md` — not to be judged on raw image generation. The human picks and refines. The AI frames and critiques; the human decides.

## Before calling it done

Hand off to the `design-critic` agent to confront `BRAND.md` against `TASTE.md`. Fix whatever reads as generic.

## Principle

Every color, font, and word traces to a stated reference or a user decision. If it traces only to "what looks good by default," it's slop — redo it.
