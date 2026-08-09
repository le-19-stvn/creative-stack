#creative Stack

An adaptive, anti-slop stack for Claude Code. Every new project — app, website, brand, content — starts from a declared point of view instead of an AI default.

Nothing by default. Everything by decision.

The problem

AI produces the average by default. Competent, coherent, and anonymous. What marks work as "AI-made" isn't that AI helped — it's that no human decision is visible in it. No angle, no taste, no choice a machine wouldn't have made on its own.

Most Claude Code starter kits make this worse: they hand you 40 skills that run on autopilot and call it a company. More output, more polished, more generic — faster.

Creative Stack does the opposite. It keeps you in the driver's seat.

How it works

Two mechanisms carry the whole thing:

1. Adaptive routing. You run /new-project, and the router detects what you're building, then mounts only the departments that project needs. A brand project pulls in design and content — and deliberately leaves off dev, finance, and legal. Nothing mounts without your say-so.

2. The taste layer. Before anything gets generated, you declare your references, your anti-references, and what you bring that a generic tool wouldn't. It's written to a TASTE.md that every department reads — and a critical reviewer confronts every output against it, sending back anything generic.

The kit doesn't supply taste. It supplies the mechanism that forces you to have one. That part is generic on purpose: your taste, not mine.

Architecture

A small always-on core routes projects and enforces the taste layer. Everything else is a department — installed disabled, enabled per project.

Plugin	Skills	Critic	Decided doc
core	new-project · taste-layer · project-charter	slop-critic	TASTE.md · CLAUDE.md
design	brand-identity · frontend-design · ui-system	design-critic	BRAND.md
dev	tech-charter · feature-build · security-review	dev-critic	STACK.md
marketing	positioning · copywriting · campaign-build	marketing-critic	POSITIONING.md
content	content-strategy · content-piece	content-critic	CONTENT-STRATEGY.md
finance	financial-assumptions · financial-model	finance-critic	ASSUMPTIONS.md
legal	legal-context · legal-doc	legal-critic	LEGAL-CONTEXT.md

Every department follows the same pattern: short, opinionated producing skills, one decided document it holds work to, and one isolated critic whose only job is to catch what's generic — or, for finance and legal, what's wrong or risky.

Install

Requires Claude Code. In the Claude Code terminal:

/plugin marketplace add <your-username>/creative-stack
/plugin install creative-stack-core@creative-stack

Then, from inside any project folder:

/creative-stack-core:new-project

Enable department plugins as the router recommends them — they install disabled and turn on per project, so you never carry weight a project doesn't need.

What each department is for

Design — brand identity, distinctive frontend, and design systems that don't read as templated. Bound to BRAND.md, checked against your taste.

Dev — forces a decided stack (STACK.md, including what's deliberately out of scope), keeps the build faithful to it, and ships a defensive security-review that scores your hardening and proposes config fixes. Delegates to language reviewers when present; never hard-depends on them.

Marketing — a positioning that names who it's not for and what it's against, copy that stays on-position, and campaign planning. The critic runs the swap test: if you can drop a competitor's name into your copy and it still fits, it says nothing.

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
