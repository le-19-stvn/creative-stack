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
7. **What we explicitly reject** — see below. This is what `design-critic` judges against, so it can't be skipped.

Output to `BRAND.md` at project root.

## What We Explicitly Reject

`BRAND.md` must carry a `## What We Explicitly Reject` section: the visual and verbal moves this brand refuses. Not taste in general — `TASTE.md` already holds that — but the ones specific to *this identity*.

Each line must be **concrete and observable**, something a reviewer can point at in a deliverable:

- "no gradient on the logo, ever — flat mono or nothing"
- "never set the display face below 24px"
- "no drop shadows; depth comes from the warm neutral layers"
- "never pair the accent with the secondary at full saturation"

Vague lines ("nothing tacky", "stay premium") are not usable — ask one follow-up for the observable form, then take what you get. Aim for 3 to 6 real rules; a short list that's meant is worth more than a long one that isn't.

Pull the ones the user already implied while deciding the palette, type, and logo above — most of them surfaced there as asides. Confirm each before writing it down.

## Load it into context

Once `BRAND.md` exists, add `@BRAND.md` to the `## Domain contracts` section of `CLAUDE.md` — on its own line, at the start of the line, **not inside a code fence** (imports inside fences are silently ignored). If the section doesn't exist yet, create it. Check the current state with your Read/Glob tools, not shell commands — OS portability.

## Note on execution

For the final logo/image render, Claude's job is to **direct**: brief, references, and critique of the rendered options against `TASTE.md` — not to be judged on raw image generation. The human picks and refines. The AI frames and critiques; the human decides.

## Before calling it done

Send `BRAND.md` to the `design-critic` agent. It sees none of this conversation — **paste the identity into the dispatch message**, don't just point at the file.

Then read its `STATUS`:

- **PASS** → done.
- **REJECT** → tell the user it came back rejected, apply **one** targeted correction from `FIX_DIRECTIVE`, re-submit once.
- **REJECT again** → **stop**. Show the last `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` verbatim. The human decides.

One automatic retry. Never a third generation, and never a silent correction — the user sees every rejection.

## Principle

Every color, font, and word traces to a stated reference or a user decision. If it traces only to "what looks good by default," it's slop — redo it.
