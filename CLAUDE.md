# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is Shukai Du's academic personal website, hosted via GitHub Pages at `shukaidu.github.io`. It is a static site with no build system, no dependencies, and no JavaScript — plain HTML and CSS only.

## Architecture

- `index.html` — Home page (bio, research interests)
- `research.html` — Research highlights with images
- `publications.html` — Full publication list
- `teach.html` — Teaching page
- `contact.html` — Contact page
- `style.css` — Single shared stylesheet for all pages
- `CV_Du.pdf` — Linked CV
- `*.png`, `*.jpg` — Research figures and profile photo referenced directly in HTML

All pages share the same navigation bar (`div.topnav`) and content wrapper (`div.main`). The active page is marked with `class="active"` on its nav link.

## Deployment

Changes pushed to the `master` branch are automatically published via GitHub Pages. There is no build step — edit HTML/CSS files directly.

## Conventions

- Each page links `style.css` via `<link rel="stylesheet" href="style.css">` (relative path).
- External links use `target="_blank"`.
- The `publications.html` list uses `<ol reversed>` with a manually set `start` attribute — update `start` when adding or removing entries.
- Special characters in author names use HTML entities (e.g., `&aacute;` for á).
- Images on `research.html` are referenced by filename only (no subdirectory) and stored at the repo root.
