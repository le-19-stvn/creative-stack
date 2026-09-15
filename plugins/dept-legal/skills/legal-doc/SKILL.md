---
name: legal-doc
description: Draft or review common legal documents from templates, bound to the project's declared legal context. Use when creating or checking an NDA, ToS/CGU/CGV, privacy policy, legal notices (mentions légales), or cookie notice for a creative-stack project. Trigger on NDA, terms of service, privacy policy, legal notice, cookie policy, contract review. Reads LEGAL-CONTEXT.md, CLAUDE.md, and TASTE.md first. Informational templates only; not legal advice.
---

# Legal Document

Produce or review a standard document from a template, fitted to declared facts. You assemble and adapt known structures; you do not invent law.

## Before drafting or reviewing

1. Read `LEGAL-CONTEXT.md`, `CLAUDE.md`, and `TASTE.md`. If `LEGAL-CONTEXT.md` is missing, run the `legal-context` skill first — no document is built on undeclared ground. (Check for and open these with your Read/Glob tools, not shell commands — OS portability.)
2. Confirm the document is **in scope** in `LEGAL-CONTEXT.md`. If it's in the out-of-scope / needs-a-lawyer section, stop and route it to a professional.
3. Fit to the declared **jurisdiction and entity**. A US ToS and an EU one with GDPR differ — use the context, don't default.

## Draft (from templates)

- **Start from a standard structure** for the document type and adapt each section to the declared facts. Fill every placeholder — an unfilled `[COMPANY NAME]` shipped as final is a defect.
- **Only clauses the context supports.** Don't add data-processing terms if no data is collected, or arbitration the jurisdiction won't honor.
- **Plain, consistent defined terms.** Define a term once, use it the same way throughout. Match the register from `TASTE.md` (sober vs accessible) without losing precision.
- **Flag every assumption inline** as `[À VÉRIFIER: …]` so nothing silent slips into a binding-looking document.

## Review (an existing document)

- Check completeness against the document type's expected clauses and against `LEGAL-CONTEXT.md`; list what's missing.
- Flag risky, overreaching, or unenforceable clauses and internal contradictions. Describe the issue; don't quietly rewrite a document someone may rely on.

## Mandatory disclaimer

Include this verbatim in every deliverable (draft or review):

> **Modèle informatif, non contractuel. Ne constitue pas un conseil juridique — faites valider par un avocat avant tout usage engageant.**

## Boundaries

- **Templates and structure only.** Do not invent statutes, cite fabricated case law, or assert what the law requires. Uncertain → mark `[À VÉRIFIER]` and route to a lawyer.
- Anything binding, high-stakes, or specialized belongs with a professional. No delegation target here (no legal agent is assumed installed) — the skill is self-contained.

## Before calling it done

Send the document to the `legal-critic` agent (always shipped with this plugin). It sees none of this conversation — **paste the full document into the dispatch message**, and name its type so the critic applies the right required-clause checklist.

Then read its `STATUS`:

- **PASS** → done.
- **REJECT** → tell the user it came back rejected, apply **one** targeted correction from `FIX_DIRECTIVE`, re-submit once.
- **REJECT again** → **stop**. Show the last `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` verbatim. The human decides — and a second rejection on a binding document is a signal to route it to a lawyer.

One automatic retry. Never a third generation, and never a silent correction — the user sees every rejection.

Every placeholder is filled or flagged, and the disclaimer is present in every deliverable, rejected or passed.
