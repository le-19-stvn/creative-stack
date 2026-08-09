---
name: frontend-design
description: Design and build distinctive frontend UI that doesn't look templated, bound to the project's taste and brand. Use when building UI, a component, a page, a React/Tailwind interface, or when the user asks to make something look better or less generic. Trigger on frontend, UI, component, layout, styling. Reads TASTE.md and BRAND.md first.
---

# Frontend Design

Build interfaces that look decided, not defaulted.

## Before writing UI

1. Read `TASTE.md` and, if it exists, `BRAND.md`. Their palette, type, and anti-references override every generic default below. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
2. Confirm the stack (React + Tailwind assumed unless told otherwise).
3. Name the register from `TASTE.md` (playful / editorial / technical…) and commit to it.

## Rules

- **Typography carries the design.** Deliberate display/body pairing, real scale. Never leave everything at default 16px.
- **Spacing is rhythm.** Consistent 4/8px scale. Whitespace reads as intent.
- **One accent, used sparingly** — the one from `BRAND.md`.
- **The one distinctive move.** Every screen needs at least one considered, non-default decision (a border treatment, an asymmetric layout, a motion) that ties to `TASTE.md`. This is where the human signature lives.
- **Accessibility is quality:** contrast ≥ 4.5:1, visible focus states, hit areas ≥ 44px.

## Anti-patterns to reject

The default three-equal-cards row as the only layout idea, centered-everything, unstyled component-library defaults shipped as final, "modern gradient" standing in for direction, lorem ipsum as final copy.

## Before calling it done

Hand to the `design-critic` agent against `TASTE.md`. If it can't point to a visible human decision, redo it.
