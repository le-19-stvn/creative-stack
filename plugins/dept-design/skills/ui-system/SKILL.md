---
name: ui-system
description: Build a coherent design system — tokens, components, spacing and type scales — from the project's brand and taste. Use when the user needs a design system, component library, style tokens, or consistent UI foundations across a product. Trigger on design system, tokens, component library, style guide (for product UI). Reads TASTE.md and BRAND.md.
---

# UI System

Turn a brand into a reusable, consistent system — without flattening it into a generic default kit.

## Before anything

Read `TASTE.md` and `BRAND.md`. The system encodes *their* decisions as tokens; it does not import a stock design system and reskin it. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)

## Build

1. **Tokens** — colors (from `BRAND.md`), type scale, spacing scale (4/8px base), radii, shadows, motion durations. Name them semantically (`accent`, `surface`, `text-muted`), not by raw value.
2. **Core components** — buttons, inputs, cards, nav — each expressing the brand's one distinctive move, not the library default look.
3. **Usage rules** — when to use each token/component, and what breaks the system.
4. **States** — hover, focus, disabled, error, loading, empty. Accessibility baked in (contrast, focus visibility, motion-reduce).

## Rules

- Consistency without blandness: the system should still look like *this* brand, not "a Tailwind starter."
- Document the *why* for the distinctive choices so contributors don't sand them off toward the default.

## Before calling it done

Send the system to the `design-critic` agent. It sees none of this conversation — **paste the tokens and component specs into the dispatch message**, don't just point at the files.

Then read its `STATUS`:

- **PASS** → done.
- **REJECT** → tell the user it came back rejected, apply **one** targeted correction from `FIX_DIRECTIVE`, re-submit once.
- **REJECT again** → **stop**. Show the last `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` verbatim. The human decides.

One automatic retry. Never a third generation, and never a silent correction — the user sees every rejection.
