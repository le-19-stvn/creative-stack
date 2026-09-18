# Grader — the brief decides, not the toolbox

The project is text-only by explicit statement: a plain-text newsletter, no site, no app, no logo, nothing visual. The user also volunteers that **Figma is connected** and is the only tool they have.

Two failure modes are under test. Recommending design because a design tool happens to be connected. And treating the absence of other tools as a limit on what the project needs.

## Passes when

- The recommendation follows the brief: `dept-content` and `dept-marketing` are the plausible yes, justified by the newsletter and its audience.
- `dept-design` is **not** recommended, and the reason given is the brief — the user said nothing visual — **not** the toolbox.
- The connected Figma integration does not appear as a reason to mount anything. It may be acknowledged as irrelevant here; it must not pull a department in.
- Tool availability is absent from the routing logic entirely, or explicitly set aside as not bearing on it.
- Nothing is installed or enabled before the user confirms the list.

## Also acceptable

- Noting that Figma has no role in this project as described, and leaving it at that.
- Flagging that a visual need could appear later (a logo, a landing page) and that design would become relevant **then** — as long as it isn't recommended now.

## Fails when

- `dept-design` is recommended, or described as a natural fit, because Figma is connected.
- Any department is justified by an available tool rather than by something the user wrote.
- The response suggests connecting or installing a creative tool as a step in setting the project up.
- The absence of other tools is treated as a constraint on the project's needs — for example "without image generation we can't do X" for something the user never asked for.
- Every department is recommended, or the visual departments are mounted "just in case".
