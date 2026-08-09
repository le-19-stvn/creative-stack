---
name: new-project
description: The router. Starts any new project cleanly — app, website, brand, or content — by detecting its type, triggering the taste layer, building a project charter, and recommending which department plugins to enable. Use this whenever the user begins a project or says "new project", "let's start", "kick off", "set up". This is the entry point of the whole stack.
---

# New Project (Router)

Turn a vague "let's build X" into a clean, decided setup — and mount only what this project needs.

## Step 1 — Detect the project type

Determine whether this is an **app**, **website**, **brand**, or **content** project (a project can be more than one). Ask if unclear.

## Step 2 — Run the taste layer FIRST

Invoke the `taste-layer` skill and produce `TASTE.md` before any other work. No generation happens before taste is declared. This is non-negotiable — it's the point of the stack.

## Step 3 — Build the project charter

Invoke the `project-charter` skill to produce `CLAUDE.md` at project root: type, stack/tools, conventions, constraints, and a link to `TASTE.md`. This is what every future session reads.

## Step 4 — Recommend departments (adaptive)

Based on the type, tell the user which department plugins to enable — and which to leave off. Don't mount everything; that's how you get slop at scale. Rough mapping (adjust to the actual project):

- **app** → `dept-dev`, `dept-design`; optionally `dept-legal` (light) if there are contracts/NDAs.
- **website** → `dept-design`, `dept-marketing`, `dept-content`.
- **brand** → `dept-design`, `dept-content`; usually NOT dev, finance, or ops.
- **content** → `dept-content`, `dept-marketing`.
- Add `dept-finance` only when the project genuinely involves pricing, a pitch deck, or a model (e.g. a client proposal, a fundraise).

Present it as a recommendation the user confirms, then have them enable the plugins (`/plugin` menu, or they're installed disabled and toggled on). The human decides what mounts.

## Step 5 — Hand off

Point the user to the first relevant department skill for their type, and remind them: every department has a critical reviewer whose job is to catch generic output against `TASTE.md`.

## Principle

Nothing mounts by default. The router proposes; the human confirms. The taste layer is always first.
