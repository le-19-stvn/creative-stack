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

## Step 4 — Recommend departments (announce only)

Based on the type, tell the user which department plugins to mount — and which to leave off. Don't mount everything; that's how you get slop at scale. Rough mapping (adjust to the actual project):

- **app** → `dept-dev`, `dept-design`; optionally `dept-legal` (light) if there are contracts/NDAs.
- **website** → `dept-design`, `dept-marketing`, `dept-content`.
- **brand** → `dept-design`, `dept-content`; usually NOT dev, finance, or ops.
- **content** → `dept-content`, `dept-marketing`.
- Add `dept-finance` only when the project genuinely involves pricing, a pitch deck, or a model (e.g. a client proposal, a fundraise).

Give one line per recommended department saying why *this* project needs it — grounded in what the user actually described, not the mapping recited back. Then name what you're leaving off and why. The refusal is part of the value; say it out loud.

At this point nothing has been executed. Wait for the user to confirm the list before Step 5.

## Step 5 — Offer to enable them (never silently)

Only after the user has seen and confirmed the list. First read the current state — it decides which command each department needs:

```
claude plugin list
```

Then ask: "Want me to run the activation commands? Each one goes through Claude Code's permission prompt — that prompt is where you approve or refuse."

Then, **one department at a time**, in the order you recommended them:

| State | Command |
|---|---|
| Not installed | `claude plugin install dept-X@creative-stack --scope local && claude plugin enable dept-X@creative-stack` |
| Installed, disabled | `claude plugin enable dept-X@creative-stack` |
| Already enabled | Skip it. Say so. |

`--scope local` mounts the department in this repository only — that's the whole point of the stack. Use `--scope user` only if the user explicitly asks for it across projects.

### Rules — non-negotiable

- The permission prompt IS the decision point. Never bypass it and never suggest allowlisting these commands.
- Chaining `install && enable` for a **single** department is fine — one department, one decision, one prompt. Never chain **two different departments** into one command: that collapses two decisions into one authorization.
- Announce each command before running it, and name the department it mounts.
- Never enable a department the user didn't confirm in Step 4.
- If a command is refused or fails, don't retry it and don't rephrase it to get a different prompt. Fall back (below) and move to the next department.

### Fallback

If execution is refused, unavailable, or errors out, print the full commands as a copyable block and let the user run them:

```
claude plugin install dept-design@creative-stack --scope local
claude plugin enable dept-design@creative-stack
```

Report honestly what got enabled and what didn't. Never report a department as mounted when its command was refused or failed.

## Step 6 — Reload, or nothing is mounted

`claude plugin` commands run outside the session, so nothing you just enabled is live yet. This step is not optional — skip it and the user will go looking for skills that aren't loaded.

Tell the user to type:

```
/reload-plugins
```

You can't run this yourself — it's a session command, not a shell command. If it warns that the reload would invalidate the prompt cache, they rerun it as `/reload-plugins --force`.

Then confirm the result: department skills appear namespaced, e.g. `/dept-design:brand-identity`.

## Step 7 — Hand off

Point the user to the first relevant department skill for their type, and remind them: every department has a critical reviewer whose job is to catch generic output against `TASTE.md`.

## Principle

Nothing mounts by default. The router proposes; the human confirms. The taste layer is always first.

The router can run the enable commands, but it never approves them. The permission prompt is the human's decision, not a formality to route around.
