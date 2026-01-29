# Project Memory & Constraints — haeusler-wein.ch

This repository contains the website for the Haeusler vineyard.

The primary goal of this project is **minimal long-term overhead**.
All technical decisions are evaluated against this goal first.

These constraints are intentional and non-negotiable unless explicitly revised.

---

## 1. Core Goals

- Minimal maintenance over time
- Predictable, boring behavior
- No operational complexity
- Changes must be easy to reason about and easy to undo

If a change improves “modernity” or elegance but increases complexity or maintenance cost, it is not acceptable.

---

## 2. Technology Constraints

- Static site only
  - Output must be plain HTML + CSS
- No JavaScript
  - No runtime JS
  - No `<script>` tags
  - No client-side frameworks
- No runtime dependencies
- No database
- No server-side logic

The site must be deployable and serveable as plain files.

---

## 3. Approved Tooling

- GitHub Pages is the deployment platform
- Jekyll is approved as the static site generator
  - Used only for:
    - layout templating (Liquid)
    - static data (`_data/*.yml`)
    - optional Markdown content (e.g. news/posts)
- No additional build tools unless explicitly approved
  - No Node tooling
  - No custom CI pipelines
  - No custom GitHub Actions

GitHub Pages’ managed Jekyll build is the only implicit tooling allowed.

---

## 4. Architecture Principles

- Prefer explicit, readable markup over abstractions
- Avoid clever or “smart” solutions
- Avoid premature generalization
- Layout and content must be clearly separated
- Desktop layout is the reference layout
- Mobile fixes must not affect desktop unless explicitly intended

Refactors are allowed only when they *reduce* long-term complexity.

---

## 5. Content Management Philosophy

- Content should live outside of HTML where practical
  - YAML data files for structured content (e.g. wines)
  - Markdown posts for chronological content (e.g. news)
- Editing content should not require understanding layout logic
- Content systems must remain:
  - static
  - transparent
  - editable with plain text tools

No dynamic CMS.
No client-side admin UI.
No hidden state.

---

## 6. Design & Visual Constraints

- No redesign unless explicitly requested
- Preserve existing visual appearance by default
- CSS classes, IDs, and layout structure should remain stable
- Visual changes must be intentional and isolated

Refactoring structure must not implicitly change design.

---

## 7. Deployment & Workflow

- Source of truth is the Git repository
- Pushing to `main` deploys the site automatically
- No manual copying of files to servers
- Structural or architectural changes must:
  - be done on a feature branch
  - go through a pull request (even for solo work)
  - be squash-merged

See `docs/deployment.md` for concrete deployment details.

---

## 8. Change Discipline

When making changes:

- Make the smallest possible change
- One logical change per commit
- Avoid touching unrelated files
- Explain *why* a change is needed before implementing it

If a change cannot be explained clearly in 2–3 sentences, it is probably too complex.

---

## 9. AI Usage (Claude / Other Tools)

AI is used as a **pair programmer**, not an autonomous agent.

Rules:
- Constraints must be stated explicitly in prompts
- AI should explain proposed changes before applying them
- AI-generated changes must be reviewed manually
- No tooling, build steps, or refactors without explicit approval

Commits represent **human approval**, not AI output.

---

## 10. Longevity Check

Before accepting any change, ask:

- Will this still make sense in 3–5 years?
- Would I be comfortable maintaining this myself?
- Does this reduce or increase long-term overhead?

If in doubt, choose the simpler option.
