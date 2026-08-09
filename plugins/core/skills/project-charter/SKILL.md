---
name: project-charter
description: Produce and maintain the project's CLAUDE.md — the single source of truth every session reads. Use this right after project type and taste are established, or whenever project conventions, stack, or constraints need to be recorded. Trigger on "set up CLAUDE.md", "project rules", "conventions", or as step 3 of new-project.
---

# Project Charter

Write the `CLAUDE.md` that anchors every future session. Without it, each session starts blind and drifts toward defaults.

## What goes in it

Keep it tight and rule-based. Fill from what the user actually said — don't invent conventions they didn't choose.

```markdown
# {{PROJECT_NAME}}

> {{ONE_LINE_GOAL}} — for {{AUDIENCE}}

## Type
{{app | website | brand | content}}

## Taste
Taste rules live in TASTE.md. Read it before producing anything visual or written.

## Stack / tools
- {{what they chose}}

## Conventions
- {{code/design/writing conventions the user stated}}

## Constraints
- {{deadlines, existing brand, tech or budget limits}}

## Departments enabled
- {{which dept-* plugins are active for this project}}

## Decisions log
- (append decisions here as they're made, so the next session inherits them)
```

## Rules

- One project, one `CLAUDE.md`. Never skip it.
- Record only decisions the user made. Options you proposed that they didn't pick don't belong here.
- Update the decisions log as the project evolves — it's what keeps continuity across sessions.
- Point to `TASTE.md` rather than duplicating it.

## Principle

The charter carries decisions, not defaults. If a line isn't something the user chose, it doesn't go in.
