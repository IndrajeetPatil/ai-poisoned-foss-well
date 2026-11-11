---
version: alpha
name: Poisoning the FOSS Well
description: >-
  Editorial and diagnostic visual identity: lime-cream canvas with faint technical grid,
  deep teal ink, Bricolage Grotesque display headings with orange-to-magenta gradient
  underlines, IBM Plex Sans body, and IBM Plex Mono code.
colors:
  primary: "{colors.ink}"
  canvas: "#fbffea"
  paper: "#f7fbdf"
  ink: "#082629"
  ink-soft: "#294448"
  panel: "#06282b"
  panel-2: "#0d373a"
  muted: "#5c6f70"
  orange: "#ff7a2f"
  amber: "#f8bd4b"
  magenta: "#e520e9"
  green: "#95f0a8"
  blue: "#72d4ff"
  red: "#ff5c73"
typography:
  display:
    fontFamily: Bricolage Grotesque, IBM Plex Sans, sans-serif
    fontSize: 1.78em
    fontWeight: 700
    lineHeight: 0.95
  heading:
    fontFamily: Bricolage Grotesque, IBM Plex Sans, sans-serif
    fontSize: 1.34em
    fontWeight: 700
    lineHeight: 0.97
  body:
    fontFamily: IBM Plex Sans, sans-serif
    fontSize: 33px
    fontWeight: 400
  mono:
    fontFamily: IBM Plex Mono, SFMono-Regular, Consolas, Liberation Mono, Menlo, monospace
rounded:
  md: 8px
shadows:
  hard: "6px 6px 0 rgba(8, 38, 41, 0.1)"
components:
  page:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
  image-artifact:
    border: "1px solid rgba(8, 38, 41, 0.34)"
    boxShadow: "6px 6px 0 rgba(8, 38, 41, 0.1), 0 12px 24px rgba(8, 38, 41, 0.1)"
    rounded: "{rounded.md}"
---

# DESIGN.md

The visual design specification of the Poisoning the FOSS Well presentation deck.

## Overview

The visual design carries an editorial and diagnostic identity: a lime-cream canvas (`#fbffea`) with a faint technical grid (`46px` pitch), deep teal ink (`#082629`), expressive Bricolage Grotesque headings marked by a vibrant orange-to-magenta gradient underline, IBM Plex Sans body typography, and IBM Plex Mono for technical and code content.

The deck format is Quarto RevealJS (`theme: simple`). Custom styles and component classes are defined in `style.css` and mirrored in the front matter above.

## Colours

- **Canvas & Neutrals:**
  - `canvas` (`#fbffea`): Overall slide backdrop patterned with a 46px technical grid line in `rgba(8, 38, 41, 0.035)`.
  - `paper` (`#f7fbdf`): Background for cards, callouts, and content surfaces.
  - `ink` (`#082629`): Deep teal used for body text, headings, and primary borders.
  - `ink-soft` (`#294448`): Muted ink for callout text and secondary reading.
  - `muted` (`#5c6f70`): Footer text and citation notes.
- **Diagnostic Accents:**
  - `orange` (`#ff7a2f`): Leading color of the signature heading gradient and warning cards.
  - `magenta` (`#e520e9`): Trailing color of the signature heading gradient and high-contrast accents.
  - `amber` (`#f8bd4b`): Caution states and flood-meter warnings.
  - `green` (`#95f0a8`): Verified states, healthy metrics, and positive callouts.
  - `blue` (`#72d4ff`): Information badges, note callouts, and technical indicators.
  - `red` (`#ff5c73`): Crisis states, poisoning vectors, and critical warnings.

## Typography

- **Headings:** `Bricolage Grotesque` (weights 500, 600, 700). High-impact headings with tight leading (`0.95`–`0.97`). Slide `h2` headings feature a signature 86px wide, 4px high gradient bar (`linear-gradient(90deg, #ff7a2f, #e520e9)`).
- **Body:** `IBM Plex Sans` (weights 400, 500, 600, 700). Readable technical sans-serif at 33px base size.
- **Code:** `IBM Plex Mono` for monospace blocks, code spans, and data labels.

## Layout & Components

- **Heading Rule:** Every `h2` receives a gradient accent line below the text, expanding to 154px on title or colored background slides.
- **Diagnostic Cards & Callouts:** Multi-colored callout boxes on `var(--well-paper)` with 8px radius, subtle border, 5px hard offset shadow, and a 6px gradient accent bar on the left edge.
- **Images & Artifacts:** Evidence screenshots and illustrations (`.hero`, `.artifact`, `.illustration`) feature a subtle border, 8px rounded corners, and a compound shadow (`6px 6px 0 var(--well-shadow)` plus `0 12px 24px rgba(8, 38, 41, 0.1)`).
- **Specialized Diagrams:** Built-in CSS widgets for `.flood-meter`, `.cost-stack`, `.business-shock`, and `.well-action-rail`.

## Do's and Don'ts

- **Do** reuse the established palette and component styling defined in `style.css`.
- **Do** keep headings in `Bricolage Grotesque` and body copy in `IBM Plex Sans`.
- **Do** preserve the subtle grid canvas and gradient accent marks.
- **Don't** introduce generic unstyled white containers or default RevealJS styles.
- **Don't** add arbitrary saturated colors outside the diagnostic palette.
