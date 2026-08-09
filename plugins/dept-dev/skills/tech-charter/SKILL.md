---
name: tech-charter
description: Force a decided technical stack instead of a defaulted one, and write it to STACK.md. Use when starting to build an app or service, choosing a framework/runtime/data layer, or when the user asks "what stack", "what should I use", "set up the project". This is the dev department's anti-slop core — the STACK.md it produces is what feature-build and dev-critic hold the code to.
---

# Tech Charter

The dev equivalent of declaring taste: nothing gets chosen by default. Produce a `STACK.md` that records **decisions**, not a shopping list of trendy tools.

Read `TASTE.md` and `CLAUDE.md` first — the project's register and constraints frame every technical call. If `TASTE.md` is missing, run the `taste-layer` skill before this one. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)

## What STACK.md must decide

Make the user choose each line, and record the *reason* — one clause, not a paragraph. If a choice is "the boring proven default," say so on purpose; that's a decision too.

- **Runtime / language** — and why this one for this project.
- **Framework** — or deliberately none. Reject "the popular one" as a reason.
- **Data layer** — store, schema approach, migrations. Or "no persistence yet."
- **Deployment / hosting** — where it runs, how it ships.
- **Testing approach** — what gets tested, at what level, with what runner.
- **The anti-dependencies** — what you deliberately refuse to add, and why. This section is the point: it's what stops kitchen-sink scope creep later.

## Rules

- **Decide, don't survey.** One choice per line with a reason. Not "options: A, B, C."
- **Boring-proven beats trendy** unless the project's taste explicitly calls for the edge. Novelty is a decision that must be justified against `TASTE.md`, never a default.
- **YAGNI at the stack level.** No auth layer, queue, cache, or microservice until a real requirement forces it. List those under anti-dependencies.
- **Constraints are first-class.** Team size, deadline, hosting limits, budget — write them down; they justify the decisions.

## Output

Write `STACK.md` at project root. Keep it short and declarative — it's read at the start of every dev session and by `dev-critic` on every deliverable. Link it from `CLAUDE.md`.

## Before calling it done

Every line traces to a reason. The anti-dependencies section is non-empty. If a section reads like a default nobody chose, redo it.
