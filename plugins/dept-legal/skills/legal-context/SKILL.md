---
name: legal-context
description: Force the project's legal ground to be declared instead of assumed, and write it to LEGAL-CONTEXT.md. Use before drafting or reviewing any legal document, or when the user asks "do we need an NDA / ToS / privacy policy", "legal setup", "what jurisdiction". This is the legal department's core — the LEGAL-CONTEXT.md it produces is what legal-doc and legal-critic hold every document to. Templates and structure only; not legal advice.
---

# Legal Context

Legal documents are wrong when they assume the wrong ground. Before drafting anything, produce a `LEGAL-CONTEXT.md` that states the project's actual legal situation — so every document is built on declared facts, not defaults.

Read `TASTE.md` and `CLAUDE.md` first for register and constraints. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)

## What LEGAL-CONTEXT.md must declare

Each line is a fact about the project, marked *confirmed* or *to verify with a lawyer*.

- **Jurisdiction(s)** — governing law and the countries where users/customers are (this drives GDPR/CCPA and consumer-law exposure).
- **Entity** — legal form and name (or "not yet incorporated"), which changes liability and signing.
- **What's being handled** — personal data collected, payments, user-generated content, minors, third-party processors. Each flags a document or clause.
- **Documents in scope** — which of NDA, ToS/CGU, privacy policy, legal notices/mentions légales, cookie notice this project actually needs, and which it doesn't.
- **Out of scope / needs a lawyer** — anything binding, high-stakes, or specialized (equity, employment, regulated sectors, litigation). Name it here so it's routed to a professional, not drafted here.

## Rules

- **Declare, don't assume.** No governing law or entity taken as default — write down the real one, or mark it *to verify*.
- **Scope down.** Only list documents the declared context actually requires. Unneeded legal boilerplate is its own kind of risk.
- **Route the hard stuff out.** If it's binding or specialized, its place here is a pointer to a lawyer, not a draft.

## What We Explicitly Reject

`LEGAL-CONTEXT.md` must carry a `## What We Explicitly Reject` section: what this project refuses to have in its documents. It's what `legal-critic` cites alongside the required-clause checks, so every line must be **concrete and pointable**:

- "no clause copied from a competitor's ToS"
- "never cite a statute or article number we haven't verified"
- "no arbitration clause"
- "never draft anything from the out-of-scope list, even as a starting point"

"Keep it safe" is not a rule. Ask one follow-up for the pointable form, then move on. Three to six lines.

## Not legal advice

This records the project's context to structure informational templates. It is not legal advice and does not determine legal obligations — a qualified lawyer does.

## Output

Write `LEGAL-CONTEXT.md` at project root. Short and declarative — read at the start of every legal session and by `legal-critic` on every document.

Then load it into context: add `@LEGAL-CONTEXT.md` to the `## Domain contracts` section of `CLAUDE.md` — on its own line, at the start of the line, **not inside a code fence** (imports inside fences are silently ignored). Create the section if it isn't there. Check the current state with your Read/Glob tools, not shell commands — OS portability.

## Before calling it done

Jurisdiction and entity are stated (or explicitly *to verify*), the in-scope documents map to real data/activity, and the out-of-scope/needs-a-lawyer section exists. If a document is listed with no reason in the context, drop it.
