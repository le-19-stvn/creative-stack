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
4. **What they explicitly reject** — see below. This one carries the most weight downstream.
5. **Non-negotiables** — a color, a font, a rule, a constraint that is theirs and fixed.
6. **Their contribution** — the key question: "What will *you* bring to this that a generic tool wouldn't think of?" Even a rough answer. This is where their signature enters.

Write it all to `TASTE.md` at project root, tagged as the user's own words where possible. Keep it short and rule-based.

### Eliciting "What We Explicitly Reject"

This is the section every critic in the kit judges against, so it has to be **checkable**. Ask: "Name the things that, if you saw them in the finished work, would make you reject it outright."

Each item must be **concrete, observable, and specific to this project** — something a reviewer can point at in a deliverable and say *there it is*. Push each answer until it reaches that form:

| Too vague | Usable |
|---|---|
| "nothing generic" | "no centered hero with the headline in the middle and the CTA underneath" |
| "not corporate" | "no stock photos of people in meetings" |
| "no AI look" | "no purple-to-blue gradient" |
| "good writing" | "never open a post with a rhetorical question" |

When an answer is vague, say so plainly and ask one follow-up: "what would that look like, concretely, so a reviewer could spot it?" One follow-up per item — take what you get and move on.

Aim for **3 to 6 items**. Stop there. This is a point of view, not a compliance questionnaire, and a long list of half-meant rules is worse than a short list of real ones. If the user has only two real rejections, record two.

Write them under a `## What We Explicitly Reject` heading in `TASTE.md`, one per line, in the user's own words. Everything else in the file can be prose; this section is a list.

## Part 2 — Load it into context

Once `TASTE.md` exists, make sure `CLAUDE.md` imports it, so every later session and every critic agent starts with the taste already in context instead of having to go find it:

Add a `## Taste — non-negotiable` section to `CLAUDE.md` containing the line `@TASTE.md` — on its own line, at the start of the line, and **not inside a code fence** (imports inside fences are silently ignored). If `CLAUDE.md` doesn't exist yet, run the `project-charter` skill. Check the current state with your Read/Glob tools, not shell commands — OS portability.

## Part 3 — Enforce the taste (during and after generation)

- Before producing anything, re-read `TASTE.md`. Every choice must trace to it. (Check for and open it with your Read/Glob tools, not shell commands — OS portability.) Do this even when the file already looks present in context: it may have changed, or context may have been compacted.
- After producing, run the confrontation: does this reflect the references and avoid the anti-references? Does it hit any line in `What We Explicitly Reject`? Does a human decision show, or is this the AI average? Name anything generic and redo it — don't wait to be asked.
- When a request would break a stated rule, flag it instead of silently overriding.
- If `TASTE.md` is silent on something that matters, ask the user to decide rather than defaulting. Don't invent the rule and don't let a critic invent it later either.

## Principle

The kit never says "this is good taste." It says "you haven't decided yet — decide." Rien par défaut, tout par décision.

A rule that can't be pointed at in a deliverable can't be enforced. Concrete rejections are what make the rest of the kit work.
