---
name: feature-build
description: Build a feature bound to the project's decided stack and taste, delegating to language-specific reviewers when available. Use when implementing a feature, endpoint, module, or fixing a bug in a creative-stack project. Trigger on build, implement, add feature, write the code. Reads STACK.md, CLAUDE.md, and TASTE.md first.
---

# Feature Build

Write code that fits the decisions already made — not framework-default scaffolding. This skill is thin on purpose: it keeps the build faithful to `STACK.md` and hands the real language work to specialists.

## Before writing code

1. Read `STACK.md`, `CLAUDE.md`, and `TASTE.md`. If `STACK.md` is missing, run the `tech-charter` skill first — nothing is built on an undecided stack. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
2. Stay inside the declared stack. **A dependency not in `STACK.md` is not yours to add** — if the feature genuinely needs one, go back and amend `STACK.md` as a decision, don't slip it in.
3. Name the smallest change that delivers the feature. YAGNI: no speculative abstraction, no layer a requirement hasn't forced.

## Build

- **Tests first.** If `tdd-guide` is available, hand off to it. Otherwise write the failing test, make it pass, refactor — same loop, done inline.
- **Match the surrounding code** — its naming, its idioms, its error-handling. New code should be unattributable as "the AI part."
- **Errors handled explicitly**, at every boundary. No silent swallow.
- **The one decision.** Even in code, the fit to this project should be visible — a chosen boundary, a deliberate data shape — not a generated template.

## Delegate the language review (portable)

Hand off to the most specific reviewer that exists in the install; skip silently if none do:

- Python → `python-reviewer` · TypeScript/JS → `typescript-reviewer` · Go → `go-reviewer` · Rust → `rust-reviewer` · React → `react-reviewer` (and the same pattern for other languages).
- No language-specific reviewer? Use `code-reviewer` if present, else review inline against `CLAUDE.md`.
- Build broken? `build-error-resolver` if present, else fix inline.

These are optional accelerators, not requirements — the skill works without any of them.

## Before calling it done

Send the change to the `dev-critic` agent (always shipped with this plugin). It sees none of this conversation — **paste the diff or the new code into the dispatch message**, don't just point at the files.

Then read its `STATUS`:

- **PASS** → done.
- **REJECT** → tell the user it came back rejected, apply **one** targeted correction from `FIX_DIRECTIVE`, re-submit once.
- **REJECT again** → **stop**. Show the last `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` verbatim. The human decides.

One automatic retry. Never a third generation, and never a silent correction — the user sees every rejection.
