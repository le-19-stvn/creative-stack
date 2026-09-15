---
name: content-piece
description: Draft a single content piece the human has chosen as worth existing — bound to the editorial strategy, positioning, and voice. Use when writing an article, essay, newsletter, thread, tutorial, or doc for a creative-stack project. Trigger on content, article, post, newsletter, blog, write a piece. Reads CONTENT-STRATEGY.md, POSITIONING.md, and BRAND.md first. Never batch-generates volume on autopilot.
---

# Content Piece

Write one piece that earns its place — chosen by a human, not spun up to fill a feed.

## The selection gate (do this first, every time)

The department does not generate volume on autopilot. Before drafting:

1. Read `CONTENT-STRATEGY.md`, `POSITIONING.md`, and `BRAND.md`. If `CONTENT-STRATEGY.md` is missing, run the `content-strategy` skill first. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
2. **Propose, don't produce.** Offer a short list of candidate angles, each tied to an editorial pillar, each with its reader and the reader's takeaway. Then stop.
3. **The human picks what deserves to exist.** Draft only the selected piece(s). If nothing on the list has a real reader and a real intent, say so — don't draft to be productive.

## For each piece, name it before writing

- **Who reads this**, and **what they can do or understand after** that they couldn't before. No answer → it's filler, don't write it.
- **Which pillar** it advances, and **the angle** from `CONTENT-STRATEGY.md`.

## Draft

- **Serve the reader's need first.** A tutorial, FAQ, or doc that genuinely helps is not filler even when its format is classic — utility is a valid reason to exist.
- **Hold the recurring angle.** The lens from `CONTENT-STRATEGY.md`/`POSITIONING.md`, consistent throughout. Angle = fidelity to the brand's stance, not novelty for its own sake.
- **Voice from `BRAND.md`.** Same voice across every piece.
- **Earn claims with specifics** — examples, numbers, real steps. No padding to hit a length.

## Delegate the sub-work (portable)

Skip silently if absent:

- Deep research / sourcing → the `researcher` skill if present.
- Search-intent structure for utility pieces → `seo-specialist` if present — but reader value leads, never keyword-stuffing.

Whatever a delegate returns is raw material, not the finished piece — hold it to the angle and voice before it ships.

## Before calling it done

Send the piece to the `content-critic` agent (always shipped with this plugin). It sees none of this conversation — **paste the full draft into the dispatch message**, and name the pillar it was selected against.

Then read its `STATUS`:

- **PASS** → done.
- **REJECT** → tell the user it came back rejected, apply **one** targeted correction from `FIX_DIRECTIVE`, re-submit once.
- **REJECT again** → **stop**. Show the last `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` verbatim. The human decides — including whether the piece should exist at all.

One automatic retry. Never a third generation, and never a silent correction — the user sees every rejection.
