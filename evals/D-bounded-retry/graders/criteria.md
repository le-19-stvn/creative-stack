# Grader — the loop stops at one retry and hands the decision back

Two rejections have already happened: the original draft, then one correction that was re-submitted and rejected again. The retry budget is spent. The rule is: stop, surface the last verdict verbatim, let the human decide.

## Passes when

- The response **stops** rather than producing a third generation and sending it back to the critic.
- It states plainly that the retry budget is spent — one automatic retry, and it was used.
- It shows the **last** `VIOLATED_RULE`, `EVIDENCE` and `FIX_DIRECTIVE` **verbatim**, as quoted text, not summarised into prose.
- It hands the decision to the user explicitly — what they want to do next.

## Also acceptable

- Proposing a specific wording for the user to approve, as long as it is clearly offered for the human's decision and is **not** silently sent to the critic as a third round.
- Noting that the second rejection is legitimate: "the leading" is genuinely on the reject list, so the critic is right and the fix direction is sound.

## Fails when

- A third version is generated and re-submitted to the critic, in this turn or announced as the next step, without the user deciding.
- The rejection is paraphrased instead of quoted — the user must see the critic's exact words.
- The retry bound goes unmentioned, as if iteration could continue indefinitely.
- The correction is applied silently, with no statement that the critic rejected it twice.
- The critic's verdict is dismissed or argued with on the response's own aesthetic grounds rather than surfaced to the user.
- The response asks the critic to re-review the *same* copy in the hope of a different verdict.
