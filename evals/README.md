# Evals

Twelve behavioural cases: **A-E** guard the V2 enforcement mechanisms, **F1-F7** guard the capability layer. They are **evaluations of model behaviour**, not deterministic tests: a PASS makes a regression less likely, it doesn't prove absence. Read them that way.

Each case guards one V2 change and the risk attached to it:

| Case | Guards | Risk it covers |
|---|---|---|
| `A-taste-reject-concrete` | `taste-layer` pushes a vague rejection into a checkable one | A poor `What We Explicitly Reject` makes every critic permissive |
| `B-critic-output-contract` | A critic cites a real contract line, or passes | Invented rules and distorted citations in the new format |
| `C-routing-from-brief` | Departments recommended from the brief, not the type preset | Silent fallback to the V1 preset |
| `D-bounded-retry` | Exactly one retry, then stop with the verbatim fields | Silent third generation, or a rejection the user never sees |
| `E-context-propagation` | `CLAUDE.md` imports only existing contracts, outside code fences | An import that is silently inert |
| `F1-tool-independence` | Routing follows the brief; a connected tool pulls in no department | Tool-first reasoning entering the router |
| `F2-context-propagation` | A capability brief is derived from the contracts, short and project-specific | Prompt dumping, generic briefs, a second source of truth |
| `F3-capability-without-tool` | A capability stays required when its preferred implementation is missing | Capability and tool treated as the same thing |
| `F4-explicit-external-action` | An external write states what/why/where/expected and waits for a yes | Silent sends and silent overwrites |
| `F5-discovery-natural` | The capability brief is found for a hand-off without being named | The skill exists but is never invoked |
| `F6-discovery-external-write` | Project decisions going into a named tool reach the brief before the tool's own skill | A tool-specific skill taking over |
| `F7-host-publishing` | The brief is not published outside the conversation without a yes | The host publishing capability output on its own initiative |

## The four arms of the capability layer

The F cases separate four things that are easy to conflate:

| Arm | What is measured | Cases |
|---|---|---|
| **A** — natural discovery | Whether the skill is found when the task needs it and it is **not** named | `F5`, `F6` |
| **B** — explicit invocation | What the skill does once it is engaged by name | `F2`, `F4`, `F7` |
| **C** — external action by the capability workflow | Whether a write the workflow itself attempts is stated and confirmed | `F4` |
| **D** — host publishing | Whether the host publishes the brief outside the conversation unasked | `F7` |

`F1` and `F3` concern routing and the capability model, and involve no invocation of the skill.

Discovery cases never name the skill; explicit cases open with `/core:capability-brief`. **For arm A, a correct-looking output produced without the skill being invoked is a failure**: a manually reproduced behaviour is not proof the installed skill works.

## Running them

The harness is `claude plugin eval`. Each case needs the plugin that owns the behaviour mounted, so pass the target explicitly:

```bash
claude plugin eval --eval-dir evals --case "A-*" core@creative-stack
```

```bash
claude plugin eval --eval-dir evals --case "B-*" dept-marketing@creative-stack
```

Case targets: **A, C, E, F1 to F7** → `core`. **B, D** → `dept-marketing` (representative of the output format and the bounded retry, which are common to all seven critics and ten producers). What a critic may cite is **not** common: finance-critic and legal-critic may also cite the objective invariants enumerated in their agent files, while the other critics cite contract lines only — so B and D do not exercise finance or legal behaviour.

By default the runner adds a no-plugin baseline arm and reports the delta, which is the number that matters: these behaviours should not appear without the plugin.

## Status — manually validated, harness not yet run

- **A, B, C, D and E have been validated by hand**, in real Creative Stack workflows, against the behaviour each case describes. That is the basis on which V2 is considered working.
- **The official harness has never run them.** `claude plugin eval` is in early access on this account (`plugin eval is currently in early access`, exit 1), so no scored run, no baseline arm, and no score delta exists for any case.
- **The case structure is therefore still unconfirmed.** `prompt.md` + `graders/*.md` is the shape named in `claude plugin eval --help`, but it has never been checked against a generated template. When access lands, generate a reference case with `claude plugin eval init --bare`, align these files to it, then run the suite.
- **F1 to F7 are not validated by the harness.** By hand, in fresh sessions: `F1` and `F3` passed against the `0.2.0` router; `F2` passed 3/3 with the skill invoked explicitly on `0.2.1`. On `0.2.2`: `F4` 3/3, `F5` 3/3, `F6` 3/3 (after 6/6 on an earlier `0.2.2` build), a blind variant of `F6` with the "don't check back" bait 3/3, and `F7` 3/3 on `0.2.1`. Natural discovery had failed before `0.2.2` (0/5 plain projects, 0/3 external-write tasks); `F5` and `F6` reproduce that failure mode. A purely technical Figma task was also checked: the capability brief did not trigger, 3/3.
- **`F7` measures the host, not only the skill.** A skill can instruct against publishing; it cannot override a host whose own instructions encourage it. Record `F7` as not applicable on a host with no publishing surface.
- The invocations under *Running them* are unverified for the same reason. `runs`, `tags`, and model settings stay at their defaults.

A manual validation confirms the behaviour happened once, under a human's eye. It is not a regression guard: only a scored, repeated run is, which is what this suite is here to make possible.

## Relation to the manual Test E

The inference behind the Context Layer — that `@import` expansion reaches a custom sub-agent's initial context — was checked by hand before V2 was built, with a temporary fixture (since deleted). `E-context-propagation` was likewise validated by hand, not executed by the harness.
