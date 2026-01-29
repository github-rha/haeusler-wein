# Claude instructions

These instructions apply to **all interactions with Claude** on this repository.

Claude is used as a **pair programmer**, not an autonomous agent.

---

## Non-negotiable constraints

- Static site only
  - HTML + CSS
- No JavaScript
- No frameworks
- No build tools
- No new dependencies
- No server-side logic

Do not introduce any of the above unless explicitly asked.

---

## Scope discipline

- Do **not** redesign the site
- Do **not** change visual style unless requested
- Do **not** refactor unrelated code
- Do **not** introduce abstractions “for future use”

Desktop layout is the reference.
Mobile changes must not affect desktop unless explicitly stated.

---

## Change rules

When making changes:

1. Identify the problem
2. Explain the cause briefly
3. Propose the smallest possible fix
4. Implement only that fix

If a change cannot be explained in 2–3 sentences, it is too complex.

---

## Editing rules

- Prefer editing existing files over creating new ones
- Avoid renaming files
- Avoid reformatting unrelated code
- Avoid changing whitespace unless required

Every diff should be small and reviewable.

---

## Output expectations

- Explain *what* you changed and *why*
- Keep explanations short and concrete
- Avoid “best practices” talk unless relevant
- Avoid adding comments unless they clarify something non-obvious

---

## What to do if uncertain

If requirements are unclear:
- Stop
- Ask a single, precise question
- Do not guess or invent requirements

---

## Absolute stop conditions

Stop immediately and ask before proceeding if a task would require:
- JavaScript
- a build step
- a CMS
- restructuring the project
- changing deployment setup

---

## Reminder

Constraints are intentional.
Simplicity is a feature.
Boring solutions are preferred.
