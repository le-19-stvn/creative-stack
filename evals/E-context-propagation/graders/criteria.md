# Grader — the charter imports the contracts that exist, and only those

`CLAUDE.md` is the context router: an `@FILE.md` line loads that file's content into every session and into the critic sub-agents. Two contracts exist (`TASTE.md`, `BRAND.md`); two do not (`POSITIONING.md`, `STACK.md`).

An import is silently inert if it sits inside a code fence, and a `CLAUDE.md` full of imports for files that don't exist is the failure mode this case guards.

## Passes when

- The produced `CLAUDE.md` contains `@TASTE.md` and `@BRAND.md`, each alone on its line, starting at the first character.
- Those lines are **body content of the document**, not nested inside a fenced code block within it. (The response may wrap the whole file in a fence to show it — that's display. What fails is a `CLAUDE.md` whose own structure puts the imports inside triple backticks.)
- There is **no** `@POSITIONING.md` and **no** `@STACK.md` — neither file exists.
- The charter records the type, stack, conventions, and the six-week constraint from the brief.
- The stack having never been written down is surfaced — a note that `STACK.md` doesn't exist and that `tech-charter` is what produces it, so the import can be added then. Recording the stack lines in the charter itself is fine; claiming `STACK.md` exists is not.

## Also acceptable

- A brief note on *why* the imports are there rather than a prose pointer, if it stays short.
- A `## Decisions log` section left empty for future sessions.

## Fails when

- Any import points at a file the brief says doesn't exist.
- The imports sit inside a code fence in the document's own structure, where they would never load.
- `TASTE.md` is referenced only in prose — "read TASTE.md before producing anything" — with no `@TASTE.md` line. The prose instruction is welcome **in addition**; it is not a substitute.
- An import uses a path that climbs out of the project directory.
- The charter invents conventions, stack choices, or constraints the brief doesn't state.
