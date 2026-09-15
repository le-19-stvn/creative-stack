---
name: financial-assumptions
description: Force every financial number to rest on a declared assumption instead of a default or a guess, and write them to ASSUMPTIONS.md. Use before building any pricing, model, forecast, or pitch-deck financials, or when the user asks "what should we charge", "build a model", "what are the projections", "TAM". This is the finance department's anti-slop core — the ASSUMPTIONS.md it produces is what financial-model and finance-critic hold every number to.
---

# Financial Assumptions

No number without a stated reason behind it. Before any model exists, produce an `ASSUMPTIONS.md` that makes every driver explicit — the opposite of a spreadsheet full of numbers nobody can defend.

Read `TASTE.md` and `CLAUDE.md` first for the project's register and constraints (a bootstrapped brand and a VC-track startup make different assumptions on purpose). (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)

## What ASSUMPTIONS.md must declare

Each line is an input with its **source and its basis** — "because X," not a number in a vacuum. Mark each as *known*, *estimated*, or *guess* so the model's confidence is honest.

- **Market basis** — how TAM/SAM/SOM is derived (bottom-up preferred: users × price, not "1% of a big number").
- **Pricing logic** — what the price is anchored to (value, cost-plus, competitor, willingness-to-pay) and why.
- **Cost drivers** — fixed vs variable, unit cost, the main cost lines.
- **Growth & conversion** — acquisition rate, conversion, churn/retention, each with its basis.
- **Cash** — runway, burn, key timing (when revenue starts, payment terms).
- **The load-bearing assumptions** — flag the 2–3 the whole model hinges on. If one breaks, the model breaks; name them.

## Rules

- **Declare, don't default.** No industry-standard number gets used silently — write down that you chose it and why.
- **Bottom-up over top-down.** Build totals from units and rates, not from a percentage of a headline figure.
- **Conservative unless justified.** Optimism is a declared choice traceable to evidence, never the default.
- **Honesty labels.** *Known / estimated / guess* on every line — a guess dressed as a fact is the core finance slop.

## What We Explicitly Reject

`ASSUMPTIONS.md` must carry a `## What We Explicitly Reject` section: the modelling moves this project refuses. It's what `finance-critic` cites alongside the arithmetic, so every line must be **concrete and checkable in a model**:

- "no top-down TAM — never '1% of a $10B market'"
- "no growth rate held constant past month 12 without a named driver"
- "never a round number without a derivation beside it"
- "no revenue line before the product ships in the timeline"

"Be realistic" is not a rule. Ask one follow-up for the checkable form, then move on. Three to six lines.

Most of these surface while declaring the drivers above — the user says "I don't want to fake a hockey stick" in passing. Write it down in the observable form and confirm it.

## Not investment advice

This declares the project's own operating assumptions. It does not recommend securities, investments, or personal financial decisions. Keep that boundary.

## Output

Write `ASSUMPTIONS.md` at project root. Short and declarative — read at the start of every finance session and by `finance-critic` on every deliverable.

Then load it into context: add `@ASSUMPTIONS.md` to the `## Domain contracts` section of `CLAUDE.md` — on its own line, at the start of the line, **not inside a code fence** (imports inside fences are silently ignored). Create the section if it isn't there. Check the current state with your Read/Glob tools, not shell commands — OS portability.

## Before calling it done

Every driver has a basis and an honesty label, totals are built bottom-up, and the load-bearing assumptions are named. If a number can't point to its assumption, it doesn't belong yet.
