<!-- .github/copilot-instructions.md - Guidance for AI coding agents working on this repo -->
# Portugal Explora — Copilot Instructions

Purpose: give an AI coding agent the essential, actionable knowledge to be immediately productive editing and extending this static website.

- Project type: simple static HTML/CSS site (no build system, no frameworks). Primary files are top-level HTML pages: `accueil.html`, `lieux.html`, `oeuvres.html`, `personnages.html` and a stylesheet under `css/style.css`.
- How pages are structured: each page is a regular HTML document using semantic sections (`header`, `main`, `footer`) and sometimes `body` `id` set to the page (example: `body id="accueil"`). Use these IDs for page-specific CSS rules.

Quick start (preview locally):

1. From the repo root run a static server, for example:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000/accueil.html` in your browser.

Notes about repository patterns and gotchas (discoverable from the files):

- CSS path inconsistency: `accueil.html` links to `style.css` at the root (`<link href="style.css">`) but the actual stylesheet is at `css/style.css`. Either update HTML to reference `css/style.css` or move/duplicate the CSS file. When modifying pages, check the `href` on the `<link>` tag.
- Image organization: images live under `images/` and a subfolder `images/Images.thomas/`. Filenames sometimes contain spaces (e.g. `Le saut du Lapin.png`). Prefer URL-friendly filenames (hyphens, lowercase) when adding or editing assets; if you must reference existing files, preserve exact names and paths.
- Empty or placeholder attributes: several `img` tags have empty `src` attributes or missing `alt` text. When adding images, set both `src` and `alt` (alt should be localized to French where appropriate).
- Language tags are inconsistent: some pages use `lang="fr"` and others `lang="en"`. Preserve or correct `lang` according to the page content (most visible content is French).

Conventions and small patterns to follow in edits:

- Keep markup simple and semantic: current pages use `figure`, `figcaption`, `article`, `section` and `nav`. Follow those elements for new content.
- Page-specific styling uses `body` `id`s (e.g., `#accueil`), so prefer adding selectors scoped to those IDs rather than adding global classes for single-page rules.
- Avoid introducing client-side frameworks or build tooling—this repo expects hand-authored static files.

Examples from the codebase to reference when changing structure:

- `accueil.html` — top-level hero, uses `body id="accueil"`, references `images/Images.thomas/portugalcarte.jpg` and currently links `style.css` in head.
- `oeuvres.html` — demonstrates site-wide nav and many `images/Oeuvres/*` assets (including names with spaces). Use this as the model for gallery/figure markup.
- `css/style.css` — currently present under `css/` (file exists but may be empty). Update this file for global styles; ensure HTML pages reference it correctly.

Developer workflows and recommendations for an AI agent:

- When previewing changes, run the static server above and open the specific page. Use the browser devtools to inspect broken image paths or missing CSS.
- When fixing a broken link or missing asset, prefer fixing the path (HTML) rather than moving large numbers of assets unless instructed.
- When renaming image files to remove spaces, update all references in HTML. Confirm by running the local server and checking pages using `oeuvres.html` and `accueil.html` which reference multiple images.

What NOT to change without the user's permission:

- Do not add build tools (npm, webpack, etc.) or convert the site to a framework. The project is intended as static HTML/CSS.
- Do not change the language of existing French content to English; maintain the page's current language unless the user asks for translation.

If you need more context or want to propose a larger refactor (e.g., unify CSS paths or normalize asset names), ask the user before making repository-wide renames.

Questions for the user (leave as comments or ask interactively):

- Should I update HTML pages to reference `css/style.css` (change `<link>`s), or would you rather move the CSS file to the repo root as `style.css`?
- Do you want filenames normalized (no spaces) under `images/` so links are easier to maintain?

End of instructions.
