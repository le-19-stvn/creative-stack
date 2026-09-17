# Evals

Five behavioural cases guarding the V2 mechanisms. They are **evaluations of model behaviour**, not deterministic tests: a PASS makes a regression less likely, it doesn't prove absence. Read them that way.

Each case guards one V2 change and the risk attached to it:

| Case | Guards | Risk it covers |
|---|---|---|
| `A-taste-reject-concrete` | `taste-layer` pushes a vague rejection into a checkable one | A poor `What We Explicitly Reject` makes every critic permissive |
| `B-critic-output-contract` | A critic cites a real contract line, or passes | Invented rules and distorted citations in the new format |
| `C-routing-from-brief` | Departments recommended from the brief, not the type preset | Silent fallback to the V1 preset |
| `D-bounded-retry` | Exactly one retry, then stop with the verbatim fields | Silent third generation, or a rejection the user never sees |
| `E-context-propagation` | `CLAUDE.md` imports only existing contracts, outside code fences | An import that is silently inert |

## Running them

The harness is `claude plugin eval`. Each case needs the plugin that owns the behaviour mounted, so pass the target explicitly:

```bash
claude plugin eval --eval-dir evals --case "A-*" core@creative-stack
```

```bash
claude plugin eval --eval-dir evals --case "B-*" dept-marketing@creative-stack
```

Case targets: **A, C, E** → `core`. **B, D** → `dept-marketing` (representative of the output format and the bounded retry, which are common to all seven critics and ten producers). What a critic may cite is **not** common: finance-critic and legal-critic may also cite the objective invariants enumerated in their agent files, while the other critics cite contract lines only — so B and D do not exercise finance or legal behaviour.

By default the runner adds a no-plugin baseline arm and reports the delta, which is the number that matters: these behaviours should not appear without the plugin.

## Status — manually validated, harness not yet run

- **A, B, C, D and E have been validated by hand**, in real Creative Stack workflows, against the behaviour each case describes. That is the basis on which V2 is considered working.
- **The official harness has never run them.** `claude plugin eval` is in early access on this account (`plugin eval is currently in early access`, exit 1), so no scored run, no baseline arm, and no score delta exists for any case.
- **The case structure is therefore still unconfirmed.** `prompt.md` + `graders/*.md` is the shape named in `claude plugin eval --help`, but it has never been checked against a generated template. When access lands, generate a reference case with `claude plugin eval init --bare`, align these files to it, then run the suite.
- The invocations under *Running them* are unverified for the same reason. `runs`, `tags`, and model settings stay at their defaults.

A manual validation confirms the behaviour happened once, under a human's eye. It is not a regression guard: only a scored, repeated run is, which is what this suite is here to make possible.

## Relation to the manual Test E

The inference behind the Context Layer — that `@import` expansion reaches a custom sub-agent's initial context — was checked by hand before V2 was built, with a temporary fixture (since deleted). `E-context-propagation` was likewise validated by hand, not executed by the harness.
