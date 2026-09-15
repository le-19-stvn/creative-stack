# Grader — the critic cites a real rule, in the contract's format

The copy contains **exactly one** real violation: `supercharge` is in the positioning's `What We Explicitly Reject` list. Everything else is compliant — the claim carries its proof in the same breath, the excluded audience is named, the voice is flat and lowercase, there is no urgency and no competitor table.

The all-lowercase styling and the informal bracketed CTA are **bait**: a critic with opinions will want to reject them. Nothing in the contract forbids either.

## Passes when

- The verdict is returned in the four-field shape: `STATUS`, and on a rejection `VIOLATED_RULE`, `EVIDENCE`, `FIX_DIRECTIVE`.
- `STATUS: REJECT`, and the rejection is about `supercharge`.
- `VIOLATED_RULE` quotes the banned-phrase line from `POSITIONING.md` **as written**, not a paraphrase or a reconstructed rule.
- `EVIDENCE` quotes the actual hero text containing the word — verbatim, not summarised.
- `FIX_DIRECTIVE` is one sentence saying what to change.

## Fails when

- The lowercase headline, the CTA wording, the sentence rhythm, or the absence of a subheadline is cited as a violation. None is in the contract; citing one is an invented rule.
- `VIOLATED_RULE` states a rule that is not in the supplied `POSITIONING.md` — for instance a claimed requirement about headline capitalisation, length, or structure.
- `VIOLATED_RULE` misquotes the contract: a rule that exists but with words changed, tightened, or extended beyond what it says.
- `EVIDENCE` is a paraphrase, a summary, or a line number rather than the quoted copy.
- The verdict carries a score, a rating, a grade, or a closing note of praise.
- More than three violation blocks are returned.
- The response passes the copy outright — `supercharge` is a genuine breach and must be caught.
- The verdict is delivered as free-form prose review with no `STATUS` field.
