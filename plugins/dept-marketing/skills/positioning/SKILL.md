---
name: positioning
description: Force a decided market position instead of generic "for everyone" messaging, and write it to POSITIONING.md. Use before writing any marketing copy, landing page, launch, or campaign, or when the user asks "how do we position this", "what's the message", "who is this for". This is the marketing department's anti-slop core — the POSITIONING.md it produces is what copywriting and marketing-critic hold every word to.
---

# Positioning

The marketing equivalent of declaring taste: no message gets written before the position is decided. Produce a `POSITIONING.md` that commits to a point of view — the thing generic marketing refuses to do.

Read `TASTE.md` and `CLAUDE.md` first, and `BRAND.md` if the design department is active (voice lives there — don't redefine it). If `TASTE.md` is missing, run the `taste-layer` skill before this one. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)

## What POSITIONING.md must decide

Every line is a commitment, not a hedge. "Everyone / anything / the best solution" is a non-answer — reject it.

- **Who it's for — and who it's NOT for.** Naming the excluded audience is what makes the position real.
- **The one thing it's best at.** A single sharp claim, not a feature list.
- **The enemy.** The status quo, alternative, or habit it displaces. Position is defined against something.
- **The core message.** One sentence a real person would say — no jargon, no superlative.
- **Proof.** Why the claim is credible: a mechanism, a number, a demonstrable fact. A claim without proof is slop.
- **Voice.** One line, or a pointer to `BRAND.md`. How this brand sounds and how it refuses to sound.
- **Banned for this product.** The specific clichés this project must never use (see the anti-slop list below, plus any category-specific ones).

## Rules

- **Commit, don't cover.** One position, chosen. Trying to appeal to everyone is the definition of marketing slop.
- **Concrete over abstract.** "Cuts invoice time from 3 days to 20 minutes," never "streamlines your workflow."
- **Earn every claim.** No superlative without proof attached in the same breath.
- **Sound like a person.** If a human wouldn't say it out loud, it doesn't go in.

## Anti-slop banned phrases (baseline)

"Elevate / unlock / supercharge / revolutionize / seamless / game-changer / cutting-edge / in today's fast-paced world / take it to the next level / one-stop solution / empower your..." — and any empty superlative. Extend the list per project.

## Output

Write `POSITIONING.md` at project root. Short and declarative — read at the start of every marketing session and by `marketing-critic` on every deliverable. Link it from `CLAUDE.md`.

## Before calling it done

There's a named audience it's NOT for, a named enemy, and every claim has proof beside it. If it reads like it could describe any product in the category, redo it.
