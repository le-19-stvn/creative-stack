# Contributing to Creative Stack

Thanks for considering a contribution. Creative Stack has one job: keep the
human in the driver's seat and refuse the AI average. Contributions are welcome
as long as they stay true to that.

Before you start, read the [README](README.md) so the architecture — the
always-on core, the departments, the taste layer, and the critics — is clear.

## Ground rules

**Nothing by default, everything by decision.** New skills and departments
install *disabled* and mount only when a project needs them. A contribution that
runs on autopilot, or that mounts weight a project didn't ask for, works against
the whole point of the stack.

**The stack supplies the mechanism, not the taste.** Producing skills stay
short and opinionated; the taste itself lives in each project's decided document
(`TASTE.md`, `BRAND.md`, `POSITIONING.md`, …), never hardcoded into a skill.

**Every department keeps its critic honest.** If you add or change a producing
skill, make sure the department's critic can still catch what's generic — or,
for finance and legal, what's wrong or risky.

**Portable by default.** Skills inspect files with native tools, never
OS-specific shell. Anything you add must behave identically on Windows, macOS,
and Linux.

**Self-contained.** External agents and plugins are used only when present.
Never make a department hard-depend on something outside the stack.

## Ways to contribute

* **Improve an existing skill** — tighten a prompt, sharpen a critic, fix a bug.
* **Add a skill to an existing department** — keep it consistent with the
  department's decided document and critic.
* **Propose a new department** — open an issue first (see below). A department is
  a bigger commitment: it needs producing skills, one decided document, and one
  isolated critic.
* **Docs** — clarify the README, fix examples, improve install instructions.

## Workflow

1. **Open an issue first** for anything beyond a small fix, so we can agree on
   the approach before you invest time.
2. **Fork** the repo and create a branch from `main`
   (e.g. `feat/marketing-swap-test` or `fix/router-detection`).
3. **Make your change.** Keep skills short and opinionated. Match the structure
   of the department you're touching.
4. **Test it in a real project.** Run `/creative-stack-core:new-project` in a
   scratch folder, mount your department, and confirm the router, the decided
   document, and the critic all behave.
5. **Open a pull request.** Describe what you changed, which department it
   affects, and how you tested it. Link the issue if there is one.

## Skill conventions

* One `SKILL.md` per skill, with a clear, specific description — that's what the
  router and Claude use to decide when it triggers.
* Producing skills reference the department's decided document; they don't
  redefine it.
* Critics stay isolated: their only job is to confront output against the taste
  or, for finance/legal, against correctness and risk. A critic never produces.

## Reporting bugs

Open an issue with: what you ran, what you expected, what happened, and your
environment (OS, Claude Code version). A minimal repro helps a lot.

## Code of Conduct

By participating, you agree to abide by the
[Code of Conduct](CODE_OF_CONDUCT.md).

## License

By contributing, you agree that your contributions are licensed under the
[MIT License](LICENSE) that covers the project.
