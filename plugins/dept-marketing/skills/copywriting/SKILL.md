---
name: copywriting
description: Write marketing copy — landing pages, emails, ads, launch announcements — bound to the project's positioning and taste, delegating to marketing/SEO agents when available. Use when writing or improving any customer-facing marketing copy, or when the user asks for a headline, landing page, campaign, or launch. Trigger on copy, headline, landing, email, ad, launch, campaign. Platform-native social posts belong to the social-post skill, not this one. Reads POSITIONING.md, TASTE.md, and BRAND.md first.
---

# Copywriting

Write copy that could only describe *this* product — not any product in its category. This skill is thin on purpose: it can delegate the drafting, but it owns the anti-slop constraint on every word that comes back.

## Before writing

1. Read `POSITIONING.md`, `TASTE.md`, and `BRAND.md` if present. If `POSITIONING.md` is missing, run the `positioning` skill first — no copy is written on an undecided position. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
2. Pull from POSITIONING: the core message, the proof, the enemy, and its `## What We Explicitly Reject` section (which carries the banned phrases). Every piece of copy advances the one position; it does not restate the feature list.
3. Pick the format's job (landing hero = one claim + proof; email = one action; ad = one hook). One idea per asset.
4. **Anything platform-native goes to `social-post`** — LinkedIn, Reddit, X, Instagram. That skill owns the channel codes; this one owns static copy. Hand it over rather than approximating the channel here.

## Write

- **Lead with the specific claim, not a warm-up.** No "In today's world…" throat-clearing.
- **Every superlative carries its proof** in the same sentence, or it's cut.
- **Concrete nouns and verbs.** Numbers, names, outcomes — never "solutions / synergies / experiences."
- **One CTA, one verb**, matched to the reader's actual next step.
- **Voice from `BRAND.md`/`POSITIONING.md`**, held consistently across every asset.

## Delegate the drafting (portable)

Hand off to whatever exists in the install; skip silently if none do:

- Broad campaign / audience / channel work → `marketing-agent` if present.
- Search-intent / on-page SEO copy → `seo-specialist` if present.
- Multi-asset launch plans → the `marketing-campaign` skill if present.

**Whatever the delegate returns is a draft, not a deliverable** — run it back through the `## What We Explicitly Reject` section of `POSITIONING.md` and the rules above before it ships. These agents optimize for generic reach; your job is to keep it on-position and un-generic. The skill works with none of them present.

## Anti-patterns to reject

Feature-listing with no positioning, empty superlatives, "for everyone" audience, generic CTA ("Learn more" as the only verb), lorem-grade filler, headline that would fit any competitor unchanged.

## Before calling it done

Send the copy to the `marketing-critic` agent (always shipped with this plugin). It sees none of this conversation — **paste the full copy into the dispatch message**, naming the asset it's for.

Then read its `STATUS`:

- **PASS** → done.
- **REJECT** → tell the user it came back rejected, apply **one** targeted correction from `FIX_DIRECTIVE`, re-submit once.
- **REJECT again** → **stop**. Show the last `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` verbatim. The human decides.

One automatic retry. Never a third generation, and never a silent correction — the user sees every rejection.
