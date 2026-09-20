# Poisoning the FOSS Well

[![Build and Deploy Presentation](https://github.com/IndrajeetPatil/ai-poisoned-foss-well/actions/workflows/build-presentation.yaml/badge.svg)](https://github.com/IndrajeetPatil/ai-poisoned-foss-well/actions/workflows/build-presentation.yaml)

This presentation examines how AI can genuinely help open-source developers move faster, triage better, and fix real bugs, while also showing how AI-generated pull requests, synthetic issue noise, collapsing trust assumptions, licence laundering, and business-model shocks are reshaping the free and open source software movement.

The deck is built with [Quarto](https://quarto.org/), rendered with RevealJS, and designed to be published as a static site.
The slide design is inspired by the [Pydantic Logfire website](https://pydantic.dev/logfire).

> [!NOTE]
> These slides were designed for ZEISS's internal FOSS Community of Practice meeting on 24th June, 2026.

## Development

This project uses Python 3.14 (see `.python-version`) with [uv](https://docs.astral.sh/uv/) for dependency management, [Quarto](https://quarto.org/) for rendering slides, and [just](https://github.com/casey/just) as a command runner.

### Prerequisites

```bash
# Install just (macOS)
brew install just
```

### Setup

```bash
just install
```

### Just Commands

```bash
just help     # Show all available commands
just install  # Install Python dependencies and the a11y extension
just update   # Update Python dependencies
just render   # Render slides to HTML
just preview  # Start a live preview with auto-reload
just open     # Alias for preview (live-reload dev server over localhost)
just clean    # Remove generated files and caches
just check    # Check the Quarto and Python setup
just axe      # Preview with an appended accessibility report
just          # Install dependencies and start live-reload preview
```

`just axe --no-browser --port 8891` forwards preview options for automated checks.

`just axe` activates `_quarto-a11y.yml`, which appends an axe-core accessibility report slide. Normal rendering keeps the checker and its report out of the published deck. Quarto commands run through `uv run` to sync the environment and discover the project Python interpreter.

### Accessibility

`just install` and the shared CI workflow install the latest
[`quarto-revealjs-a11y`](https://github.com/mcanouil/quarto-revealjs-a11y) directly
from upstream with `quarto add mcanouil/quarto-revealjs-a11y --no-prompt`.
The extension handles browser zoom, slide isolation, focus indicators, link
underlines, reduced motion, and screen-reader announcements.

Run `just install` again after `just clean`, which removes installed extensions.

The `accessibility.html` helper still handles scrollable code, slide-menu focus,
and vertical-slide semantics. Unused tabset handling has been removed.
The extension's slide-menu patch and accessibility settings panel are disabled
as in the reference deck: version 0.2.3 introduces ARIA and contrast failures in
those components.

Use `just axe` to inspect slides, fragments, and menu panels in presentation and
scroll views. Normal builds omit the axe checker.

## Feedback

Feedback and suggestions are welcome in [the issue tracker](https://github.com/IndrajeetPatil/ai-poisoned-foss-well/issues).

## Acknowledgements

The deck text, layout, and repository-authored material are released under CC0.

Third-party photographs and screenshots remain under their original terms and are included with attribution:

- Title slide photograph: [Daniel Prado / Unsplash](https://unsplash.com/photos/old-wishing-well-in-a-grassy-field-with-trees-U08P3HTx3SI)
- "Why LLMs tilt the field" photograph: [Maxim Tolchinskiy / Unsplash](https://unsplash.com/photos/oil-is-polluting-the-surface-of-the-water-Gt4DBSXqySc)
- Screenshots of articles, GitHub issues, repository pages, and websites are included for commentary, criticism, and source attribution

## License

Repository-authored material is released under the terms of the [CC0 1.0 Universal](LICENSE) license. Third-party images are not relicensed under CC0.
