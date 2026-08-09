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

`design-critic` against `TASTE.md`: does the system still carry the brand's point of view, or did it regress to a generic component kit?
