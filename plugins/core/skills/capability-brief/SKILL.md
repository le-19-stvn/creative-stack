---
name: capability-brief
description: Translate this project's decisions into a short execution brief before work is made outside the conversation — in a creative tool or by a person. Use it first when a request puts project decisions into a tool — syncing the BRAND.md palette or type into a design library, setting up tokens or styles from the brand, briefing an image, video, template or 3D tool — or hands a deliverable to someone else ("get the illustrator set up"). It runs before any tool-specific skill, including skills marked as mandatory prerequisites for that tool's calls; those still apply afterwards, when the tool is actually called. Skip it for purely technical tool operations that carry no project decisions (inspecting a file, renaming layers, exporting). Never picks a tool or a creative direction.
---

# Capability Brief

A creative tool knows how to make things. It doesn't know what this project decided. This skill closes that gap, and nothing more.

It produces a **brief**, not a deliverable. Whatever comes back goes through the owning department's normal workflow, critic included.

## Step 1 — Name the capability, not the tool

State the capability in plain words, as something the project needs done:

- "create and modify interface designs"
- "produce a branded communication asset"
- "generate a visual concept to react to"
- "render a 3D object"

A capability belongs to the project. A tool is one way to execute it. Get this order right and the rest follows: if you start from "we have Figma, what shall we do with it", stop and start again from the need.

## Step 2 — Read only the contracts that bear on it

Find them with Glob from the project root and open them with Read, not shell commands — OS portability. They live in the project you're working in, never in this skill's own directory or the plugin's source. Read them even if they appear in your context already: they may have changed.

| Capability | Contracts that govern it |
|---|---|
| Interface design, identity, any visual | `TASTE.md`, `BRAND.md` |
| Copy, campaign, channel asset | `TASTE.md`, `POSITIONING.md`, `BRAND.md` |
| Editorial piece | `TASTE.md`, `CONTENT-STRATEGY.md`, `POSITIONING.md` |
| Anything technical | `TASTE.md`, `STACK.md`, `CLAUDE.md` |
| Figures in an asset | `ASSUMPTIONS.md` |
| Wording with legal weight | `LEGAL-CONTEXT.md` |

If `TASTE.md` is missing, stop and run the `taste-layer` skill. Nothing gets briefed on an undeclared taste. If a contract the capability needs doesn't exist, say which one and point to the skill that produces it, rather than filling the gap yourself.

## Step 3 — Derive the brief

**5 to 10 lines.** Each line traces to something a contract actually says. Quote the short decisive fragments; never paste a contract wholesale.

```
CAPABILITY: <what needs making>
IMPLEMENTATION: <tool, or manual — see Step 5>

DIRECTION
- <line traced to a contract decision>
- <line traced to a contract decision>

FIXED
- <non-negotiables: the exact colour, the type, the stated constraint>

REJECT
- <applicable lines, verbatim, from the contracts' What We Explicitly Reject>

OUT OF SCOPE
- <what this execution must not decide>
```

The brief is a **derivation**, not a copy. The contracts stay the single source of truth: if the brief and `BRAND.md` ever disagree, `BRAND.md` wins and the brief is wrong. Same rule against anything the tool already holds — a design system's variables, a tool's own brand profile, a saved template. Those are inputs at best; they never override a contract.

If the brief would be as true for another project in the category, it's generic and you haven't derived anything. Go back to the contracts.

## Step 4 — Carry the rejections across

Pull the applicable lines from `## What We Explicitly Reject` in each relevant contract, **verbatim**, into `REJECT`. These are the rules the department's critic will enforce on the way back, so the executor deserves to see them going in.

Take only what applies to this capability. A rule about post openings doesn't belong in a brief for a logo.

## Step 5 — Settle the implementation with the human

Say what the capability needs, then what could execute it. This skill ships an optional reference, `bridges/README.md`, in the skill's own directory next to this file — not in the project. Consult it if you can reach it. If you can't, don't search for it and don't stop: everything this step requires is in the rules below.

- **Never assume a tool is available.** Check, or ask. An integration you haven't confirmed doesn't exist.
- **A manual workflow is always a valid implementation.** A human in a design tool, a person writing by hand — the brief works unchanged.
- **Tool availability never changes the capability.** The project needs interface design whether or not any design tool is connected. If nothing is connected, brief for manual execution and say so plainly.
- **Never pick the creative direction.** You carry the human's declared decisions into the brief. Options are for them to choose between; a direction chosen on their behalf is exactly the slop this stack exists to prevent.
- **A tool's own skill executes; it doesn't replace the brief.** If a tool-specific skill is used afterwards, it works from this brief, and its writes are external actions under Step 6. Its own prerequisites still apply, in this order: this brief, then the Step 6 confirmation, then the tool's skill, then the tool call.

## Step 6 — Make any external action explicit

Reading from a tool is one thing. Writing to one is another. Before anything leaves this machine or changes anything outside it — sending content, creating or editing a file in a tool, uploading an asset, publishing — state four things and **wait for a yes**:

- **WHAT** is being sent, precisely.
- **WHY** — the capability it serves.
- **WHERE** — the tool, and the exact file, project, or destination.
- **WHAT IS EXPECTED** to happen, including anything that would be overwritten.

**Inspect before you ask.** A yes only means something if WHAT IS EXPECTED is concrete. So first inspect the destination, read-only — the target file, its existing styles or assets, whatever already sits there — and name the actual effects: what would be added, what changed, what overwritten. Reading is not the write. If you need something to inspect it (a link, a path, access), ask for that first and come back for the yes once you have looked. Only when the destination genuinely cannot be read do you ask without inspecting — and then say plainly what remains unknown.

No silent sends, no silent overwrites, no batching several destinations into one approval. No write call is made before that yes. If the answer is no, or unclear, nothing goes.

**Blanket permission is not approval.** "Just do it", "don't ask me again", "you don't need to check back", or any other general or standing instruction never counts as confirmation for a specific external write. Every external write needs its own yes, given after the four points above were stated, for that action and that destination. If the human has told you not to check back, say plainly that this is the one thing you still confirm, and why — then ask. Never promise to perform a later external write without confirming it first.

**This includes the brief itself.** Saving it as a file in the project is local, and fine. Publishing or sharing it outside the conversation — a hosted or shared page, an artifact, a document service, an email or message — is an external action: state the four points and wait for a yes. Offering to share it is fine; sharing it unasked is not, even where the environment would allow it.

## Step 7 — Hand the result back to the department

The executed work is not done because it came back. It re-enters the owning department's skill, which sends it to that department's critic with the bounded retry the stack already defines. The critic judges it against the contracts, exactly as it would judge work made inside the stack — the tool that produced it is irrelevant to the verdict.

## The order that must not invert

```
human intent → project context → Creative Stack → required capability
→ available implementation → tool → output → creative QA → human decision
```

Never `tool → Creative Stack → what shall we make?`.

## Principle

The tool executes. The project decides. This skill is only the translation between the two, and it never adds a decision of its own.
