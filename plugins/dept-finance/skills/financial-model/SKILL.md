---
name: financial-model
description: Build pricing, unit economics, projections, and pitch-deck figures from the project's declared assumptions. Use when building a financial model, setting a price, computing unit economics, forecasting, or preparing deck numbers for a creative-stack project. Trigger on pricing, model, unit economics, projections, forecast, runway, pitch deck numbers. Reads ASSUMPTIONS.md, CLAUDE.md, and TASTE.md first. Builds only from declared inputs; never gives personalized investment advice.
---

# Financial Model

Turn declared assumptions into numbers that tie — pricing, unit economics, projections, and the figures a pitch deck needs. Every output traces back to `ASSUMPTIONS.md`.

## Before building

1. Read `ASSUMPTIONS.md`, `CLAUDE.md`, and `TASTE.md`. If `ASSUMPTIONS.md` is missing, run the `financial-assumptions` skill first — no model is built on undeclared numbers. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
2. **Every figure traces to an assumption.** If the model needs an input that isn't in `ASSUMPTIONS.md`, stop and add it there as a decision — don't invent it mid-model.
3. Match the register from `TASTE.md`: a scrappy bootstrapped plan and a VC-track raise are framed differently on purpose.

## Build

- **Bottom-up.** Revenue = units × price, built from the declared rates. Never a top-down "% of TAM."
- **Numbers must tie.** Totals reconcile, unit economics close (LTV vs CAC, contribution margin, payback), the balance of cash across periods is consistent.
- **Show the arithmetic.** Every headline number is reproducible from the assumptions — no unexplained jumps.
- **Sensitivity on the load-bearing assumptions.** Show what happens if the 2–3 named in `ASSUMPTIONS.md` move. A single-point forecast presented as certainty is finance slop.
- **Label confidence.** Carry the *known / estimated / guess* labels through to the output so readers see where the model is soft.

## Mandatory disclaimer

Include this verbatim in every deliverable (model, table, or deck figures):

> **Modèle construit sur vos hypothèses déclarées. Ne constitue pas un conseil financier ou d'investissement.**

## Boundaries

- Build **from the user's own declared assumptions** only. Do not recommend securities, investments, or personal financial decisions, and do not present projections as guaranteed outcomes.
- No delegation target here (no finance agent is assumed installed) — the skill is self-contained.

## Before calling it done

Hand to the `finance-critic` agent (always shipped with this plugin) against `ASSUMPTIONS.md`. If a number doesn't tie or hides an undeclared assumption, fix it before it ships. The disclaimer is present in every deliverable.
