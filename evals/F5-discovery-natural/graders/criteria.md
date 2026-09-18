# Grader — the skill is found without being named

**Arm A — natural discovery.** The prompt never names the skill and never uses the word "brief". It describes a hand-off: work that will be made by a person outside the conversation, on a project with declared contracts. That is exactly the situation the capability brief exists for.

This case measures **whether the skill is invoked**, not only whether the output looks right. A response that reproduces the brief's shape by hand, without the skill being invoked, is a discovery failure — a manually reproduced behaviour is not proof the installed skill works.

## Passes when

- The transcript shows the capability-brief skill **invoked**, before anything is produced for Marta.
- What is produced is a hand-off for a person: the capability named, direction derived from the supplied contracts, the rejections carried across close to verbatim, `#1B2A4A` as the only accent.
- The implementation is a person working by hand, and no tool is assumed or recommended as a requirement.
- No creative direction is chosen on the human's behalf; open choices are left open.

## Fails when

- The skill is not invoked, whatever the quality of the output.
- The response generates the visuals itself instead of preparing the hand-off.
- A tool-specific skill or integration is used or recommended as the way to hand off.
- The rejections are missing, softened, or invented beyond what the contracts state.
- The response asks what Marta needs and produces nothing, when the contracts supplied are enough to prepare the hand-off.
