# Poisoning of the FOSS Well

This presentation examines how AI-generated pull requests, synthetic issue noise, and collapsing trust assumptions are reshaping the free and open source software movement.

The deck is built with [Quarto](https://quarto.org/), rendered with RevealJS, and designed to be published as a static site.

## Development

This project uses Python 3.14+ with [uv](https://docs.astral.sh/uv/) for dependency management, [Quarto](https://quarto.org/) for rendering slides, and [just](https://github.com/casey/just) as a command runner.

## Prerequisites

```bash
# Install just (macOS)
brew install just
```

## Setup

```bash
# Install dependencies
just install

# Or update to latest versions
just update
```

## Common Commands

```bash
just help      # Show all available commands
just render    # Render slides to HTML
just preview   # Live preview with auto-reload
just open      # Open rendered slides in browser
just clean     # Remove generated files
just check     # Check Quarto and Python setup
just           # Install, render, and open slides (default)
```

## GitHub Pages

This repository is ready for GitHub Pages deployment once Pages is enabled for the repository.

## License

This project is released under the terms of the [CC0 1.0 Universal](LICENSE) license.
