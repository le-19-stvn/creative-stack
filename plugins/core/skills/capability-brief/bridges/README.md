# Implementations

A reference for `capability-brief`. It lists what a capability might be executed with. **Nothing here is a dependency.**

No bridge is implemented in this release. Creative Stack sends no content anywhere by itself, and a project is complete without any of these tools connected.

## How to read this

Left column: what the project needs done — that belongs to the project, and the owning department.
Middle: tools that can serve it, when one is actually connected and you have confirmed it.
Right: the fallback that always works.

| Capability | Possible implementation | Always valid |
|---|---|---|
| Create or modify interface designs | a design tool (e.g. Figma) | manual design workflow |
| Build or extend a design system | a design tool with variables or tokens | hand-written tokens in the repo |
| Produce a branded communication asset | a template-based asset tool (e.g. Canva) | manual layout |
| Generate a visual concept to react to | an image generation tool | sketch, moodboard, or commissioned work |
| Produce a moving asset | a video generation or editing tool | storyboard handed to a human editor |
| Render a 3D object or scene | 3D software (e.g. Blender) | brief handed to a 3D artist |
| Write or adapt copy | the stack's own marketing and content skills | a person writing it |

## Rules

- **The capability is required; the tool is not.** If no implementation is available, the brief goes to a human and the project continues.
- **The tool never earns a department.** Canva is not a department; the work belongs to design, marketing, or content depending on the task. Same for every other tool.
- **The tool never earns a critic.** Output is judged against the project's contracts, whatever produced it. There are no tool-specific quality standards.
- **Verify before designing around it.** Confirm an integration exists, and confirm whether it can read, write, or both, before a brief assumes any of it.
- **A tool's own stored brand data is not a contract.** Templates, saved palettes, design-system variables, tool-side brand profiles: inputs at most. `BRAND.md` and the other contracts remain the source of truth.

## Adding an implementation

Add a row. That's the whole procedure. A new implementation needs no new skill, no new department, no new critic, and no change to any contract — if it seems to need one, the capability was probably described as a tool.
