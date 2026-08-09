---
name: taste-layer
description: Capture the human point of view for a project before any generation happens, and enforce it afterwards. Use this skill at the start of any creative or product work — design, brand, UI, copy, content, naming — and whenever a request would otherwise be answered with a generic default. Trigger when the user starts a project, asks for design/brand/content, or says things like "make it good", "not generic", "with taste". Produces and maintains a TASTE.md the whole stack reads.
---

# Taste Layer

This is the anti-slop mechanism. Its job is not to add taste — it's to force the *human* to declare theirs, then hold every output to it. The kit supplies the mechanism; the user supplies the taste. Nothing here encodes one person's preferences as a default.

## Why this exists

AI produces the *average* by default: coherent, competent, and anonymous. What marks work as "made by AI" isn't that AI helped — it's that no human decision is visible in it. This skill makes the human decision a required, recorded step so it can't be skipped.

## Part 1 — Elicit the taste (before any generation)

Do NOT generate visuals, copy, or design until `TASTE.md` exists for the project. Interview the user to fill it. Ask in small batches, never all at once. Cover:

1. **References they love** — 2-5 specific examples (sites, brands, products, artists) and, for each, *what specifically* they admire. "I like Linear" is useless; "Linear's restraint — one accent, tons of whitespace, no decoration" is signal.
2. **Anti-references** — what they refuse. What looks cheap, generic, or "AI-made" to them. This is often more discriminating than what they like.
3. **The feeling** — three adjectives the finished thing should evoke, and three it must NOT.
4. **Non-negotiables** — a color, a font, a rule, a constraint that is theirs and fixed.
5. **Their contribution** — the key question: "What will *you* bring to this that a generic tool wouldn't think of?" Even a rough answer. This is where their signature enters.

Write it all to `TASTE.md` at project root, tagged as the user's own words where possible. Keep it short and rule-based.

## Part 2 — Enforce the taste (during and after generation)

- Before producing anything, re-read `TASTE.md`. Every choice must trace to it. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
- After producing, run the confrontation: does this reflect the references and avoid the anti-references? Does a human decision show, or is this the AI average? Name anything generic and redo it — don't wait to be asked.
- When a request would break a stated rule, flag it instead of silently overriding.
- If `TASTE.md` is silent on something that matters, ask the user to decide rather than defaulting.

## Principle

The kit never says "this is good taste." It says "you haven't decided yet — decide." Rien par défaut, tout par décision.
