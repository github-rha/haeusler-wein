# Architecture — haeusler-wein.ch

## System boundaries

```
  ┌────────────────────────────────────┐
  │  Visitor's browser                 │
  │                                    │
  │  Loads HTML + CSS + images only.   │
  │  No JavaScript runtime.            │
  └────────────────┬───────────────────┘
                   │ HTTPS
                   ▼
  ┌────────────────────────────────────┐
  │  GitHub Pages                      │
  │  Serves the Jekyll-built static    │
  │  site for haeusler-wein.ch.        │
  └────────────────┬───────────────────┘
                   │ git push to main
                   ▼
  ┌────────────────────────────────────┐
  │  GitHub repo (source of truth)     │
  │  github.com/github-rha/haeusler-   │
  │  wein                              │
  └────────────────────────────────────┘
```

The repository **is** the application. There is no server, database, or
backend service. The deployed site is plain files served by GitHub Pages'
CDN.

---

## Technology constraints

- **Static site only** — output is plain HTML + CSS.
- **No JavaScript** — no `<script>` tags, no runtime JS, no client-side frameworks.
- **No runtime dependencies.**
- **No database.**
- **No server-side logic.**

The site must be deployable and serveable as plain files.

---

## Approved tooling

- **GitHub Pages** is the deployment platform.
- **Jekyll** is approved as the static site generator, used only for:
  - layout templating (Liquid)
  - static data (`_data/*.yml`)
  - optional Markdown content
- **No additional build tools** unless explicitly approved:
  - No Node tooling
  - No custom CI pipelines
  - No custom GitHub Actions

GitHub Pages' managed Jekyll build is the only implicit tooling allowed.

---

## Repository layout

```
  haeusler-wein/
  ├── _config.yml          Jekyll config
  ├── _data/
  │   └── content.yml      All page text and structured content
  ├── _layouts/
  │   └── default.html     Page shell, nav, footer
  ├── images/              Photos and icons
  ├── index.html           The single page (sections: about, wine, contact, legal)
  ├── styles.css           All styling
  ├── CNAME                haeusler-wein.ch
  ├── robots.txt
  ├── sitemap.xml
  └── docs/                This documentation
```

Content lives in `_data/content.yml`; layout lives in `_layouts/` and
`index.html`. Editing content does not require touching layout.

---

## Architecture principles

- Prefer explicit, readable markup over abstractions.
- Avoid clever or "smart" solutions.
- Avoid premature generalization.
- Layout and content are separated: structured content in YAML, presentation in Liquid + CSS.
- **Desktop layout is the reference.** Mobile fixes must not affect desktop unless explicitly intended.

Refactors are allowed only when they *reduce* long-term complexity.

---

## Content management

- Content lives outside HTML where practical:
  - YAML data files for structured content (wines, contact, legal text).
  - Markdown for any future chronological content.
- Editing content does not require understanding layout logic.
- Content systems remain **static, transparent, and editable with plain text tools**.

No dynamic CMS. No client-side admin UI. No hidden state.

---

## Design constraints

- No redesign unless explicitly requested.
- Existing visual appearance is preserved by default.
- CSS classes, IDs, and layout structure remain stable.
- Visual changes are intentional and isolated.

Refactoring structure must not implicitly change design.
