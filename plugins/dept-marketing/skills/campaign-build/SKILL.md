---
name: campaign-build
description: Plan a marketing campaign or launch — the objective, audience, channel mix, asset list, and sequence — bound to the project's positioning. Use when planning a launch, a multi-asset campaign, an email sequence, or a channel plan. Trigger on campaign, launch, go-to-market, sequence, channel plan, rollout. Reads POSITIONING.md, TASTE.md, and CLAUDE.md first. Plans the campaign; hands each asset's actual copy to the copywriting skill.
---

# Campaign Build

Own the campaign's shape — what ships, on which channels, in what order, toward one objective. This skill plans; it does **not** write the final words. Per-asset copy belongs to the `copywriting` skill, so a campaign never fragments into interchangeable best-practice tactics.

## Before planning

1. Read `POSITIONING.md`, `TASTE.md`, and `CLAUDE.md`, plus `BRAND.md` if the design department is active. If `POSITIONING.md` is missing, run the `positioning` skill first — nothing is campaigned on an undecided position. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
2. Name the **one objective** (launch, sign-ups, waitlist, re-engagement). One campaign, one job.
3. Pull the audience and the core message from `POSITIONING.md` — the whole campaign carries that single through-line.

## Plan

- **One spine.** Every asset advances the same positioning promise. If a piece needs a different message, it's a different campaign — don't blur them.
- **Channels by fit, not by default.** Choose only the channels the audience and message actually justify. Being on every channel is how a campaign turns generic.
- **Asset list, each with one job.** A landing page persuades, a nurture email advances, a launch post announces. Name each asset and its single job; don't let one asset try to do all three.
- **Sequence and timing.** Order the assets into a rollout (tease → launch → follow-through) with realistic timing tied to `CLAUDE.md` constraints. The sequence is the campaign; a pile of assets is not.
- **One CTA per asset**, mapped to its stage in the funnel.

## Hand off the copy

For each asset, hand the actual writing to the `copywriting` skill — it binds the words to `POSITIONING.md`, filters the declared rejections, and can delegate drafting. This skill stays at the plan level; it does not produce final copy itself.

Social assets go to `social-post` instead — it holds the per-channel codes for LinkedIn, Reddit, X, and Instagram, and keeps the form adapted without letting the position drift. Name the channel and the asset's one job; it does the rest.

## Before calling it done

Send the plan to the `marketing-critic` agent. It sees none of this conversation — **paste the full plan into the dispatch message**: objective, channel mix, asset list, sequence.

Then read its `STATUS`:

- **PASS** → done.
- **REJECT** → tell the user it came back rejected, apply **one** targeted correction from `FIX_DIRECTIVE`, re-submit once.
- **REJECT again** → **stop**. Show the last `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` verbatim. The human decides.

One automatic retry. Never a third generation, and never a silent correction — the user sees every rejection.
