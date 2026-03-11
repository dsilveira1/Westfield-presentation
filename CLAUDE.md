# CLAUDE.md — Westfield Presentation Repository

## Project Overview

This repository contains the **"Intelligent Presentation Layer"** — a strategic presentation for Westfield Capital Management that proposes replacing static document production (PowerPoint/PDF) with AI-generated HTML presentations powered by Claude + MCP infrastructure.

The presentation itself serves as a proof-of-concept: it is a single-page HTML document that demonstrates the kind of polished, interactive, branded output the initiative aims to produce at scale.

## Repository Structure

```
.
├── index.html          # Main presentation — single-file HTML with embedded CSS/JS
├── WIP/
│   └── index.html      # Work-in-progress placeholder for future iterations
├── README.md           # Minimal project readme
└── CLAUDE.md           # This file
```

## Architecture & Technology

### Single-File HTML Presentation (`index.html`)

The entire presentation is a self-contained HTML file with no external dependencies beyond Google Fonts. It includes:

- **Embedded CSS** (~550 lines) — All styles are in a `<style>` block in `<head>`
- **Embedded JavaScript** (~20 lines) — Scroll progress bar and intersection observer for fade-in animations
- **No build system** — No bundler, preprocessor, or framework. Edit and open in browser.
- **No external JS libraries** — Vanilla JavaScript only

### Design System (CSS Custom Properties)

All colors and fonts are defined as CSS custom properties in `:root`:

| Variable         | Value                    | Usage                        |
|------------------|--------------------------|------------------------------|
| `--navy`         | `#0D1B2A`               | Primary background           |
| `--navy-mid`     | `#162236`               | Card backgrounds             |
| `--navy-light`   | `#1E3050`               | Hover / highlighted cards    |
| `--teal`         | `#1A9E8F`               | Primary accent (labels, borders) |
| `--teal-light`   | `#22C4B2`               | Emphasis text                |
| `--gold`         | `#C9A84C`               | Quote accents                |
| `--red`          | `#E05252`               | "Before" / problem indicators |
| `--white`        | `#F4F6F8`               | Primary text                 |
| `--serif`        | Cormorant Garamond       | Headings, large numbers      |
| `--sans`         | DM Sans                  | Body text                    |
| `--mono`         | DM Mono                  | Labels, tags, eyebrows       |

### Presentation Sections

The document follows a numbered section structure:

1. **Hero** — Title, subtitle, key metrics
2. **01 · The Problem** — Cost grid showing storage/time waste
3. **Quote Block** — CTO quote on legacy systems
4. **02 · The Shift** — Before/after comparison grid
5. **03 · How It Works** — Architecture flow diagram (Eze → Snowflake → Airia MCP → Claude → HTML)
6. **04 · Use Cases** — Four use case cards (client reviews, prospects, internal, board)
7. **05 · Implementation Path** — Four-phase rollout plan
8. **06 · The Ask** — Summary and ROI metrics

### Key CSS Patterns

- **`.fade-in` / `.visible`** — Scroll-triggered animations via IntersectionObserver
- **`.cost-grid` / `.cost-card`** — Metric cards with colored left borders
- **`.ba-grid` / `.ba-panel`** — Before/after comparison layout
- **`.arch-flow` / `.arch-node`** — Horizontal architecture diagram
- **`.use-grid` / `.use-card`** — Feature/use-case cards
- **`.phase-list` / `.phase-item`** — Numbered implementation phases
- **`.quote-block`** — Gold-accented blockquote
- **`.divider`** — Gradient horizontal rule between sections

## Development Workflow

### Editing

1. Edit `index.html` directly — all markup, styles, and scripts are in one file
2. Open in any modern browser to preview (no server required)
3. Use browser DevTools for live CSS tweaking

### Conventions

- **No build step** — Changes are immediate upon file save
- **No external dependencies** — Keep the file self-contained (Google Fonts loaded via CDN is the only external resource)
- **Responsive design** — Uses `clamp()` for fluid typography and `auto-fit` grids; a `768px` breakpoint exists for the before/after grid
- **Color semantics** — Red (`--red`) = problems/before state; Teal (`--teal`) = solutions/after state; Gold (`--gold`) = quotes/emphasis
- **Typography hierarchy** — Serif for headlines and large numbers; Sans for body; Mono for labels and tags
- **Section numbering** — Sections use the pattern `0X · Title` in `.section-label` elements

### When Making Changes

- Preserve the Westfield brand identity (navy/teal/gold palette, font choices)
- Keep all assets inline — no separate CSS or JS files
- Maintain the `fade-in` class on content elements for scroll animations
- Use existing CSS custom properties rather than hardcoding colors
- Follow the established card/grid patterns for new content sections
- Test at multiple viewport widths; the layout uses responsive grids

## Git Workflow

- **`main`** — Primary branch (remote)
- **`master`** — Local branch with presentation content
- Feature branches use the `claude/` prefix
- Commit messages should be descriptive of content changes

## Context: Business Domain

This presentation argues for Westfield Capital Management to adopt AI-generated HTML as a first-class output format in their Claude + MCP sprint. Key domain terms:

- **MCP** — Model Context Protocol (AI tool/data access layer)
- **Airia** — Governed AI access platform
- **Eze / APX** — Portfolio management and transaction systems
- **Snowflake** — Cloud data warehouse
- **WIP 2.0** — Legacy internal project referenced as becoming obsolete
- **Phase 4 Connect Sprint** — Timeline reference for client-facing rollout
