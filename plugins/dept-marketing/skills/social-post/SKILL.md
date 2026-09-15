---
name: social-post
description: Write platform-native social posts — LinkedIn, Reddit, X/Twitter, Instagram — adapting the form to each channel while holding the position declared in POSITIONING.md. Use when writing or adapting a post, thread, carousel, or comment for a social network, or turning an existing article into channel-native posts. Trigger on LinkedIn, Reddit, X, Twitter, Instagram, post, thread, carousel, social. Reads POSITIONING.md first and refuses to write without it.
---

# Social Post

Say the same thing on every channel, in the way each channel actually reads. One writer per network lives in `platforms/` — what they share is the law below.

## The law — form is yours, substance is not

You adapt hook, length, structure, and rhythm to the channel. The claim, the audience, the enemy, the proof, and the voice come from `POSITIONING.md` and do not move. There is no "LinkedIn tone" — there is *this brand's* position, said in a way LinkedIn reads.

**When a channel's best practice conflicts with the position, the position wins.** Every time. A post that performs and says nothing has failed. If a format genuinely can't carry the position, say so and recommend a different channel — that's a valid, useful output.

## Before writing

1. Read `POSITIONING.md`, plus `TASTE.md` and `BRAND.md` if present. **If `POSITIONING.md` is missing, stop** — nothing gets published on an undecided position. Point to the `positioning` skill and go no further. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
2. Pull the core message, the proof, the enemy, the named audience, and its `## What We Explicitly Reject` section (which carries the banned phrases). Those five travel unchanged to every channel.
3. Settle source or no source (below).
4. Name the platforms, then read `platforms/<name>.md` for each one you're writing — that file only.

## Adapt an existing piece, or write short-form direct

`dept-content` may or may not be mounted. Both paths are normal; never require the content department.

- **With a source piece** — the user names it, or you find one with Glob. Adapt it: **the post adds no claim the source doesn't make.** It carries one idea from the piece and points to it; it isn't a summary and it doesn't replace the read.
- **Without one** — write short-form straight from `POSITIONING.md`. No source is needed to post.
- If `CONTENT-STRATEGY.md` exists, hold its recurring angle. Reference it, never redefine it — angle and voice are owned upstream.

## Writing for several channels at once

Same substance, different form per channel — that's the whole exercise. **Never paste one post across networks.** Identical copy on two channels is the symptom this skill exists to remove: either the form was never adapted, or the substance was flattened to fit everywhere at once.

## Guardrails

- **No invented metrics.** Never state or imply expected reach, impressions, engagement, or follower growth. You don't know them. Describe channel mechanics as mechanics, never as promised outcomes.
- **No fabricated social proof.** No invented testimonial, user count, or "trusted by" claim. Every number traces to the proof in `POSITIONING.md`, or it doesn't appear.
- **Platform rules outrank performance.** Each `platforms/` file opens with its community rules. They aren't suggestions, and breaking them costs more than any post is worth.
- **No engagement bait.** Manufactured outrage, fake vulnerability, "comment X and I'll send it", follow-for-follow. That's the algorithm's voice, not the brand's.

## Delegate (portable)

Skip silently if absent:

- Broad channel/audience strategy → `marketing-agent` if present.
- The rollout these posts belong to → the `campaign-build` skill.
- Visual direction for image-led channels → the design department if mounted; `BRAND.md` governs, not your own taste.

Whatever a delegate returns is raw material. They optimize for reach; you hold the position.

## Before calling it done

Send the post to the `marketing-critic` agent (always shipped with this plugin). It sees none of this conversation — **paste the post into the dispatch message**, and name the platform and the source piece it was adapted from. Without the source, the critic can't tell whether the position drifted.

Then read its `STATUS`:

- **PASS** → done.
- **REJECT** → tell the user it came back rejected, apply **one** targeted correction from `FIX_DIRECTIVE`, re-submit once.
- **REJECT again** → **stop**. Show the last `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` verbatim. The human decides.

One automatic retry. Never a third generation, and never a silent correction — the user sees every rejection.
