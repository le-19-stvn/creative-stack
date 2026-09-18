---
name: project-charter
description: Produce and maintain the project's CLAUDE.md — the single source of truth every session reads, and the context router that loads the project's contracts. Use this right after project type and taste are established, or whenever project conventions, stack, or constraints need to be recorded. Trigger on "set up CLAUDE.md", "project rules", "conventions", or as step 3 of new-project.
---

# Project Charter

Write the `CLAUDE.md` that anchors every future session. Without it, each session starts blind and drifts toward defaults.

`CLAUDE.md` does two jobs. It records the decisions, and it **loads the contracts** — so taste and domain rules are already in context rather than waiting for someone to remember to read them.

## What goes in it

Keep it tight and rule-based. Fill from what the user actually said — don't invent conventions they didn't choose.

```markdown
# {{PROJECT_NAME}}

> {{ONE_LINE_GOAL}} — for {{AUDIENCE}}

## Type
{{app | website | brand | content}}

## Taste — non-negotiable
@TASTE.md

Read TASTE.md before producing anything visual or written.

## Domain contracts
@BRAND.md
@POSITIONING.md

## Work made outside this session
Before project decisions go into an external tool, or a deliverable is handed off for someone else to make, run the `capability-brief` skill first. Tool-specific skills execute from that brief; they don't replace it.

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

## The contracts section

`@FILE.md` is not a pointer — Claude Code expands the imported file and loads its **content** into context at launch, for this session and for the critic agents it dispatches. That is why the contracts go here rather than being merely mentioned.

Import only the contracts that **exist right now**. One line each, `@` first character, nothing else on the line:

- `@TASTE.md` — always, as soon as the taste layer has run.
- `@BRAND.md`, `@STACK.md`, `@POSITIONING.md`, `@CONTENT-STRATEGY.md`, `@ASSUMPTIONS.md`, `@LEGAL-CONTEXT.md` — each one only once its department skill has actually produced it.

Check which ones exist before writing the section, with your Read/Glob tools, not shell commands — OS portability. Omit the rest: a department that was never mounted has no contract to load, and an import is added by the skill that creates the contract, not in advance.

### Two writing traps

- **Imports inside a code fence are inert.** The template above is fenced for display only. In the real `CLAUDE.md` the `@` lines sit in normal document body, at the start of the line, never inside triple backticks. If you fence them, nothing loads and the failure is silent.
- **Keep contracts at project root.** An import that points outside the working directory triggers an approval dialog. All contracts live at root, so keep the paths bare — `@TASTE.md`, not a relative path out of the tree.

## Rules

- One project, one `CLAUDE.md`. Never skip it.
- Record only decisions the user made. Options you proposed that they didn't pick don't belong here.
- Import the contracts; don't restate them. The charter carries project decisions, the contracts carry their own rules.
- Never import a file that doesn't exist yet, and never leave an import behind for a contract that was removed.
- Update the decisions log as the project evolves — it's what keeps continuity across sessions.

## Maintenance

When a department later produces its contract, add the matching import line to `CLAUDE.md`. Each contract skill owns that step, but if you notice a contract at root with no import, add it and say so.

Imports resolve **at session launch**. A contract created mid-session is on disk but not yet in context, which is exactly why every producer and critic also carries an explicit instruction to read its contract. That duplication is deliberate: reliability over DRY.

## Principle

The charter carries decisions, not defaults. If a line isn't something the user chose, it doesn't go in.

Context beats instruction. A contract that is loaded doesn't depend on anyone deciding to open it.
