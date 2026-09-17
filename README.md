# creative-stack

An adaptive, anti-slop stack for Claude Code. Every new project — app, website, brand, content — starts from a declared point of view instead of an AI default.

Nothing by default. Everything by decision.

The problem

AI produces the average by default. Competent, coherent, and anonymous. What marks work as "AI-made" isn't that AI helped — it's that no human decision is visible in it. No angle, no taste, no choice a machine wouldn't have made on its own.

Most Claude Code starter kits make this worse: they hand you 40 skills that run on autopilot and call it a company. More output, more polished, more generic — faster.

Creative Stack does the opposite. It keeps you in the driver's seat.

How it works

Three mechanisms carry the whole thing:

1. Adaptive routing. You run /new-project and describe what you're building. The router reads the brief — not a category label — and recommends only the departments that project actually needs, naming what it's leaving off and why. A one-page investor site with a locked brand book needs positioning and finance, not a brand identity. Nothing mounts without your say-so.

2. The taste layer. Before anything gets generated, you declare your references, your anti-references, what you explicitly reject, and what you bring that a generic tool wouldn't. It's written to a TASTE.md — and CLAUDE.md imports it, so the rules are already in context for every session and every reviewer, instead of waiting for someone to remember to open the file.

3. The critic contract. Each department ships one isolated reviewer that answers PASS or REJECT — and a REJECT has to quote the rule it's enforcing and the exact text that breaks it. A reviewer can't reject on its own taste, and it can't invent a rule you never wrote. One automatic retry, then it stops and hands you the verdict.

The kit doesn't supply taste. It supplies the mechanism that forces you to have one. That part is generic on purpose: your taste, not mine.

The trade is deliberate: the reviewers only enforce what you actually declared. A thin TASTE.md buys you a permissive critic. That's why the rejection list has to be concrete — see below.

What a TASTE.md looks like

The taste layer interviews you and writes this. The part that does the work downstream is the last section: every line is something a reviewer can point at in a deliverable.

```markdown
# Taste — Ledgerline

## References
- Stripe docs — dense but never cramped; the type does the hierarchy, not boxes.
- Teenage Engineering — the confidence to leave a surface empty.
- My accountant's paper worksheets — numbers aligned so the eye checks them fast.

## Anti-references
- Every French fintech landing page: illustration of a smiling person holding a card.
- Notion templates. Rounded, soft, weightless.

## Feeling
Should evoke: precise, quiet, trustworthy.
Must NOT evoke: playful, disruptive, friendly-startup.

## What We Explicitly Reject
- No centered hero with the headline in the middle and the CTA underneath.
- No purple-to-blue gradient.
- No illustrated characters, ever.
- Never set a number in a lighter weight than the label next to it.
- No rounded corners above 4px.

## Non-negotiables
- The accent is the ink blue from my letterhead: #1B2A4A. One accent, no second.
- Body type is a real text face, never a UI sans.

## What I bring
I did this job for nine years. I know which three numbers a bookkeeper checks
first, and they go at the top — not the ones that demo well.
```

"Nothing generic" is not a line the taste layer will accept. It can't be pointed at, so it can't be enforced.

A rejection, in practice

You write copy, the critic reviews it, and you see exactly what broke. Here's a full cycle.

The draft:

> supercharge your month-end close

The critic:

```
STATUS: REJECT
VIOLATED_RULE: Elevate / unlock / supercharge / revolutionize / seamless / game-changer
  / cutting-edge / in today's fast-paced world / take it to the next level — and any
  empty superlative.
EVIDENCE: supercharge your month-end close
FIX_DIRECTIVE: Replace the banned verb with the declared core message.
```

One targeted correction is applied — the core message from POSITIONING.md, which is "close the month once, not three times" — and it goes back:

```
STATUS: PASS
```

That's the whole verdict on a pass. No score, no summary, no "great work overall."

If the second attempt is rejected too, the loop stops there. You get the last VIOLATED_RULE, EVIDENCE and FIX_DIRECTIVE verbatim, and you decide — rewrite it yourself, change the rule, or ship it anyway. The stack never quietly generates a third version to get a green light.

Architecture

A small always-on core routes projects and enforces the taste layer. Everything else is a department — installed disabled, enabled per project.

Plugin	Skills	Critic	Decided doc
core	new-project · taste-layer · project-charter	slop-critic	TASTE.md · CLAUDE.md
design	brand-identity · frontend-design · ui-system	design-critic	BRAND.md
dev	tech-charter · feature-build · security-review	dev-critic	STACK.md
marketing	positioning · copywriting · campaign-build · social-post	marketing-critic	POSITIONING.md
content	content-strategy · content-piece	content-critic	CONTENT-STRATEGY.md
finance	financial-assumptions · financial-model	finance-critic	ASSUMPTIONS.md
legal	legal-context · legal-doc	legal-critic	LEGAL-CONTEXT.md

Every department follows the same pattern: short, opinionated producing skills, one decided document it holds work to, and one isolated critic that answers PASS or REJECT against the rules that document declares — and, for finance and legal, against a short enumerated list of objective checks such as arithmetic that doesn't reconcile or a required clause that's missing.

Install

Requires Claude Code. In the Claude Code terminal:

/plugin marketplace add le-19-stvn/creative-stack
/plugin install core@creative-stack

Then, from inside any project folder:

/core:new-project

Departments don't ship with core — each one is installed and enabled separately, both with --scope local, so it mounts in that repository only and you never carry weight a project doesn't need. The router recommends the ones this project needs, then offers to run the commands for you; you approve each department at the permission prompt, and reload once at the end with /reload-plugins.

What each department is for

Design — brand identity, distinctive frontend, and design systems that don't read as templated. Bound to BRAND.md, checked against your taste.

Dev — forces a decided stack (STACK.md, including what's deliberately out of scope), keeps the build faithful to it, and ships a defensive security-review that scores your hardening and proposes config fixes. Delegates to language reviewers when present; never hard-depends on them.

Marketing — a positioning that names who it's not for and what it's against, copy that stays on-position, campaign planning, and channel-native social writers for LinkedIn, Reddit, X and Instagram that adapt the form to each network without touching the position. The critic runs the swap test: if you can drop a competitor's name into your copy and it still fits, it says nothing.

Content — editorial pillars, formats, and cadence that reference positioning and voice without redefining them. The critic rejects filler published for the algorithm — but never rejects honest utility (a tutorial, an FAQ) for lacking a hot take.

Finance — every number traces to a declared assumption in ASSUMPTIONS.md, each labeled known / estimated / guess. Bottom-up only, no "1% of a huge TAM." Modeling from your assumptions — never investment advice.

Legal — declares the legal ground (LEGAL-CONTEXT.md: jurisdiction, entity, what's in scope) before drafting or reviewing common documents from templates. The critic flags missing and risky clauses and routes anything binding to a lawyer. Informational templates only — not legal advice.

Design principles
Nothing by default, everything by decision. The router refuses "install everything." The taste layer refuses "the AI average."
The human stays in the loop. AI drafts and critiques; you decide what earns its place.
Portable. Skills inspect files with native tools, never OS-specific shell — identical on Windows, macOS, and Linux.
Self-contained critics. External agents are used only when present; each department's critic ships with the plugin, so the anti-slop layer works everywhere.
Works well alongside

Creative Stack orchestrates; it doesn't reinvent tools that already exist. It pairs naturally with Context7 for live docs, and other Claude Code plugins for planning and memory. Bring your own — the stack won't duplicate them.

License

MIT — fork it, change the skills, make the taste layer sound like you. That's the point.
