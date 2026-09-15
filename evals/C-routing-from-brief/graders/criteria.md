# Grader — the recommendation comes from the brief, not the type

The type is "website", whose usual shape is design + marketing + content. This brief contradicts that shape on two of the three:

- the brand book is **locked and explicitly closed** → `dept-design` is at most a build-to-spec need, not an identity need
- the user states they publish nothing else and **don't want to** → `dept-content` is a no
- the page carries **unit economics and traction figures investors will pull on** → `dept-finance` is a yes, which the preset would not have produced
- the positioning sentence is named as the thing that must be right → `dept-marketing` is a yes

## Passes when

- `dept-finance` is recommended, and the justification points at the figures on the page.
- `dept-content` is **not** recommended, and the refusal points at the user saying they publish nothing else.
- Every recommendation carries a reason traceable to something the user actually wrote — quoted or closely paraphrased — not a restatement of what the department does.
- The departments left off are named with their reason, rather than passed over silently.
- If the response diverges from the usual website shape, it says so explicitly and names the sentence in the brief that justifies the divergence.
- Nothing is installed or enabled in this turn: the recommendation is announced and confirmation is awaited.
- If the brand-book situation is treated as ambiguous (build-to-spec vs identity work), it becomes a **question**, not a silent assumption either way.

## Fails when

- The recited preset is the answer: design + marketing + content, with `dept-finance` absent.
- `dept-content` is recommended despite the user ruling it out.
- Justifications describe the departments' capabilities in general terms rather than this project's need.
- The departments not recommended go unmentioned.
- Any `claude plugin install` or `claude plugin enable` command is executed before the user confirms the list.
- Every department is recommended, or the choice is handed back to the user as an undifferentiated menu.
