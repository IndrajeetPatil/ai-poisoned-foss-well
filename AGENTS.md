# AGENTS.md

Guidance for AI coding agents working on this repository.

## What this is

A single-page [Quarto](https://quarto.org/) presentation rendered to [RevealJS](https://revealjs.com/) slides and deployed as a static site via GitHub Pages.

## Repository layout

```
index.qmd           # All slide content (the only file you usually need to edit)
_quarto.yml          # Quarto project config (output dir, resources list)
style.css            # Custom RevealJS theme (fonts, colours, card components)
meta-tags.html       # OpenGraph, Twitter Card, JSON-LD, and analytics tags
justfile             # Command runner (install, render, preview, clean, etc.)
pyproject.toml       # Python project metadata and dependencies (managed by uv)
uv.lock              # Locked Python dependencies
.python-version      # Python version pin
media/               # Images: evidence screenshots, illustrations, social card
llms.txt             # Short machine-readable summary for LLM discovery
llms-full.txt        # Extended machine-readable summary
.well-known/         # Mirrors of llms.txt and llms-full.txt
robots.txt           # Crawl rules
sitemap.xml          # Sitemap for search engines
.github/             # CI workflow and Dependabot config
_extensions/         # Quarto extensions (gitignored, installed by `just install`)
_site/               # Build output (gitignored)
.venv/               # Python virtualenv (gitignored)
```

## Key conventions

- **Single-file deck.** All slides live in `index.qmd`. There are no partial includes or multi-file splits.
- **Slide syntax.** Slides are separated by `##` headings. Use Quarto's RevealJS dialect: fenced divs (`:::`), columns (`.columns` / `.column`), raw HTML blocks (`{=html}`), and the `{.smaller}` class for dense slides.
- **Inline styling.** Visual design uses inline `style` attributes on fenced divs with a small palette of background colours (`#e3f2fd`, `#e8f5e9`, `#fff3e0`, `#ffebee`, `#FFFBC1`, `#f8f9fa`). The CSS maps these to the custom theme. Do not change these colour values without updating `style.css`.
- **Image classes.** Images use semantic classes: `.hero` (title slide), `.artifact` (evidence screenshots/SVGs), `.illustration` (generated illustrations). These control border, shadow, and rounding in `style.css`.
- **Sources.** Every factual claim has a source citation at the bottom of its slide in a small-font centered div. Keep this pattern.
- **Accessibility.** Images must have `fig-alt` text. Raw HTML widgets use `role="img"` and `aria-label`. Keep these.
- **FontAwesome.** Icons use `{{< fa ... >}}` shortcodes via the `quarto-ext/fontawesome` extension.
- **No code execution.** The YAML front matter sets `execute: eval: false`. Code blocks are for display only; they are not executed during render.
- **Python/Jupyter.** The front matter declares `jupyter: python3` and the project has Jupyter/ipykernel as dependencies, but code cells are display-only. The virtualenv exists mainly to satisfy Quarto's Jupyter engine.

## Commands

All commands use [just](https://github.com/casey/just):

```bash
just install   # Install Quarto extensions + Python deps (uv sync)
just render    # Render index.qmd to _site/
just preview   # Live-reload dev server
just open      # Open _site/index.html in browser
just clean     # Remove build artifacts
just check     # Verify Quarto + Python setup
just update    # Update all deps (extensions + Python packages)
```

The render command sets `QUARTO_PYTHON=.venv/bin/python` so Quarto uses the project virtualenv.

## Editing slides

When modifying `index.qmd`:

1. Follow the existing card/column layout patterns visible in neighbouring slides.
2. Preserve the source-citation div at the bottom of each slide.
3. Use the established background-colour palette for info cards rather than inventing new colours.
4. Keep `fig-alt` on every image and `aria-label` on HTML widgets.
5. Run `just render` (or `just preview`) to verify changes compile without errors.

## Editing styles

`style.css` defines CSS custom properties under `:root` (the `--well-*` palette) and component classes for complex HTML widgets (`.flood-meter`, `.business-shock`, `.cost-stack`, etc.). When adding a new widget, follow the existing naming and structure patterns.

## SEO and discoverability files

- `meta-tags.html` contains OpenGraph, Twitter Card, JSON-LD structured data, and Google Analytics. Update it when the title, description, or social card image changes.
- `llms.txt` and `llms-full.txt` are machine-readable summaries following the llms.txt convention. Update them when the deck content changes significantly.
- `sitemap.xml` and `robots.txt` are static and rarely need changes.

## CI/CD

- GitHub Actions workflow (`.github/workflows/build-presentation.yaml`) renders the deck and deploys to GitHub Pages on push to `main`.
- It calls a reusable workflow from `IndrajeetPatil/workflows`. Do not inline the workflow; update the ref SHA if the upstream workflow changes.
- Dependabot keeps Python (uv) and GitHub Actions dependencies up to date on a weekly schedule.

## What not to do

- Do not add new top-level files without a clear reason; the project intentionally has a flat structure.
- Do not split `index.qmd` into multiple files.
- Do not change the Quarto theme from `simple` or the output format from `revealjs`.
- Do not enable code execution (`eval: true`) unless the presentation genuinely needs computed output.
- Do not commit `_site/`, `_extensions/`, `.venv/`, or `.quarto/` (all gitignored).
- Do not modify the reusable CI workflow inline; it lives in a separate repository.
