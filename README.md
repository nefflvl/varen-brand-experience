# VAREN® Brand Experience

Brand narrative, identity system, and interactive design grid for VAREN — elite performance golf.

**Live site:** [varen-brand-experience.pages.dev](https://varen-brand-experience.pages.dev)

## Design Grid System

This project is built on the **VAREN Harmonic 4-Column Modular Grid** — a Swiss/International typographic grid derived from the VAREN Harmonic Grid&trade; &mdash; a &phi;-derived Swiss/International typographic system.

**Every design decision must conform to the grid.** See [GRID-SYSTEM.md](GRID-SYSTEM.md) for the complete specification.

### Quick Reference

| Property | Value |
|----------|-------|
| Aspect ratio | 16:9 (1280 × 720pt source) |
| Columns | 4 equal, 20.45pt gutters |
| Baseline | 15px horizontal rows |
| Margins | 2.77% sides, 4.92% top, 12.5% bottom (asymmetric) |
| Type scale | ×1.333 / ×1.5 alternating (perfect 4th / 5th) |
| Leading | Constant 1.176× ratio |
| Spacing | Fibonacci (8, 13, 21, 34, 55, 89, 144, 233px) |

### Type Families

| Role | Family | Source |
|------|--------|--------|
| Editorial serif | Signifier | Klim Type Foundry (licensed) |
| Functional sans | Söhne | Klim Type Foundry (licensed) |
| Display narrow | Söhne Schmal | Klim Type Foundry (licensed) |
| Technical mono | Söhne Mono | Klim Type Foundry (licensed) |

### Grid Overlay

Press the **Grid** button (bottom-right of page) to toggle the live grid overlay showing columns + baseline rows.

## How to Update the Live Site

1. Edit `index.html` in this folder
2. Open **GitHub Desktop**
3. Write a short summary (e.g. "v2.2 — Söhne fonts, GSAP animations")
4. Click **Commit to main**
5. Click **Push origin**

Site updates automatically in ~30 seconds via Cloudflare Pages.

## Version History

| Version | Description |
|---------|-------------|
| v1.0 | Launch. Swiss grid, golden ratio type, mk1 logo lockups |
| v2.0 | Remove "Bible", speed→tempo, foundation details |
| v2.1 | VAREN Harmonic grid variables, Buzzworthy scroll animations |
| v2.2 | Söhne fonts, GSAP ScrollTrigger, grid overlay, nav scramble |
| v2.3 | Buzzworthy frame layouts, 16:9 horizontal grid, Signifier numerals |

## Local Backups

The `versions/` folder contains HTML snapshots of every completed version. These stay on your Mac only — never uploaded to GitHub or deployed.

## Stack

- **Typography**: Signifier · Söhne · Söhne Schmal · Söhne Mono (all Klim)
- **Grid**: VAREN Harmonic 4-column modular, 15px baseline, 16:9 frames
- **Animation**: GSAP 3.12 + ScrollTrigger
- **Spacing**: Fibonacci scale (8, 13, 21, 34, 55, 89, 144, 233px)
- **Logo**: VAREN® Logo Kit mk1 — Half-Y, Thirds, Vertical, Insignia
- **Deploy**: Cloudflare Pages — static, no build, auto-deploys from `main`
