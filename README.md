# Poisoning the FOSS Well

This presentation examines how AI can genuinely help open-source developers move faster, triage better, and fix real bugs, while also showing how AI-generated pull requests, synthetic issue noise, collapsing trust assumptions, licence laundering, and business-model shocks are reshaping the free and open source software movement.

The deck is built with [Quarto](https://quarto.org/), rendered with RevealJS, and designed to be published as a static site.

## Contents

The current deck covers:

- acknowledged benefits of AI when used transparently by maintainers and contributors
- FOSS as a hidden economic subsidy for the software industry
- Pull-request pollution and maintainer overload
- Security exploitation through synthetic issue noise and agent speed
- Economic extraction from FOSS without reciprocal support
- Tailwind CSS as a warning about AI breaking documentation-driven FOSS businesses
- Provenance collapse, clean-room reimplementation, and licence laundering
- Hallucinated packages as a new supply-chain vector
- Trust collapse after XZ Utils and the resulting damage to the contributor pipeline
- Mitchell Hashimoto's trust-gating approach with Ghostty and Vouch
- Community adaptability through technical counter-measures and policy shifts
- The social costs borne by maintainers, junior developers, and the movement itself

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
just install  # Install Quarto extensions and Python dependencies
just update   # Update Quarto extensions and Python dependencies
just render   # Render slides to HTML
just preview  # Start a live preview with auto-reload
just open     # Open rendered slides in the default browser
just clean    # Remove generated files and caches
just check    # Check the Quarto and Python setup
just          # Install dependencies, render, and open slides
```

## Feedback

Feedback and suggestions are welcome in [the issue tracker](https://github.com/IndrajeetPatil/ai-poisoned-foss-well/issues).

## Asset Attribution

The deck text, layout, and repository-authored material are released under CC0.

Third-party photographs and screenshots remain under their original terms and are included with attribution:

- Title slide photograph: [Daniel Prado / Unsplash](https://unsplash.com/photos/old-wishing-well-in-a-grassy-field-with-trees-U08P3HTx3SI)
- "Why LLMs tilt the field" photograph: [Maxim Tolchinskiy / Unsplash](https://unsplash.com/photos/oil-is-polluting-the-surface-of-the-water-Gt4DBSXqySc)
- Screenshots of articles, GitHub issues, repository pages, and websites are included for commentary, criticism, and source attribution

## Licence

Repository-authored material is released under the terms of the [CC0 1.0 Universal](LICENSE) licence. Third-party images are not relicensed under CC0.
