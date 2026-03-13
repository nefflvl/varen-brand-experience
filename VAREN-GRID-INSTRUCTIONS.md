# VAREN® Harmonic Grid System — Design Instruction Set

## MANDATORY: Read this document before making ANY design, layout, or typography decisions.

This document codifies the VAREN grid system derived from three authoritative sources:

1. **Josef Müller-Brockmann** — *Grid Systems in Graphic Design* (the "Bible" of Swiss grid layout)
2. **Stephen Kelman** — 4-Column Modular Grid System for 16:9 digital presentations (stephenkelman.co.uk)
3. **VAREN Harmonic Grid™** — φ-derived 12-column system merging both traditions

Every design decision on this site MUST conform to this instruction set.

---

## 1. THE GOLDEN RATIO FOUNDATION

φ (phi) = 1.618033988749895

Every measurement in the VAREN system traces back to φ:

| Derivation | Formula | Result |
|---|---|---|
| Canvas aspect | 16:9 ≈ φ² | 2.618 ≈ 2.56 |
| Side margins | 720 / φ⁴ / 3 | 35.451pt → 2.77% |
| Top margin | 35.451 / 720 | 4.924% |
| Bottom margin (asymmetric) | 90 / 720 | 12.5% |
| Gutter | baseline × φ⁻² | 15 × 1.3634 ≈ 20.451pt → 1.28rem |
| Baseline grid | φ × 9.27 | ≈ 15pt → 15px |
| Leading constant | 1.176× | All type sizes × 1.176 = line-height |
| Spacing sequence | Fibonacci | 8, 13, 21, 34, 55, 89, 144, 233px |

---

## 2. THE 12-COLUMN MODULAR GRID

### Kelman's 4 φ-Macro Columns × 3 Swiss Micro = 12 Columns

The grid is built on Kelman's 4-column landscape presentation system, subdivided into 12 for web flexibility.

```
┌─── φ-A ───┬─── φ-B ───┬─── φ-C ───┬─── φ-D ───┐
│  1  2  3  │  4  5  6  │  7  8  9  │ 10 11 12  │
└───────────┴───────────┴───────────┴───────────┘

φ-A = Columns 1–3   (25% of content width)
φ-B = Columns 4–6   (25% of content width)
φ-C = Columns 7–9   (25% of content width)
φ-D = Columns 10–12 (25% of content width)
```

### CSS Implementation

```css
.frame-inner {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 0 var(--grid-gutter);  /* 1.28rem = 20.451pt */
  max-width: var(--content-max);
  padding: var(--grid-margin-top) var(--grid-margin-x) var(--grid-margin-bottom);
}
```

### Column Placement Rules

| Content Type | Grid Columns | Kelman Macro | Width |
|---|---|---|---|
| Section labels (with horizontal lines) | 1 / -1 | Full width | 100% |
| Section titles (h2) | 1 / 7 | φ-A + φ-B | 50% |
| Body prose (7-10 words/line) | 1 / 9 | φ-A + φ-B + φ-C | 67% |
| Narrow prose (~1/3 width) | 1 / 5 | φ-A + partial φ-B | 33% |
| Intro/lead text | 1 / 7 | φ-A + φ-B | 50% |
| Sub-grids (cards, tables) | 1 / -1 | Full width | 100% |
| 3-column cards | span 4 each | 1 φ-macro each | 33% |
| 4-column cards | span 3 each | 1 Swiss micro each | 25% |
| 2-column layout | span 6 each | 2 φ-macro each | 50% |
| Sidebar/aside content | 10 / 13 | φ-D | 25% |

---

## 3. THE KELMAN TYPE SCALE

### Scale Steps (Alternating ×1.333 Perfect Fourth / ×1.5 Perfect Fifth)

| Step | Name | Size (pt) | CSS rem | Leading (pt) | Leading/Size | CSS Variable |
|---|---|---|---|---|---|---|
| 1 | Display | 68 | 5.25rem | 80 | 1.176× | --type-h1 |
| 2 | H1 | 59.5 | 4.59rem | 70 | 1.176× | — |
| 3 | H2 | 51 | 3.94rem | 60 | 1.176× | --type-h2 (≈3.25rem) |
| 4 | H3 | 38.25 | 2.95rem | 45 | 1.176× | --type-h3 (≈2.5rem) |
| 5 | H4 | 25.5 | 1.97rem | 30 | 1.176× | --type-h4 (2rem) |
| 6 | Body/Lead | 19.125 | 1.48rem | 22.5 | 1.176× | --type-lead (1.5rem) |
| 7 | Body | 12.75 | 0.98rem | 15 | 1.176× | --type-body (1.25rem) |
| 8 | Caption | 9.5625 | 0.74rem | 11.25 | 1.176× | --type-caption (0.75rem) |

### Critical Rule: The 1.176× Leading Constant

**ALL type sizes use 1.176× leading.** This is Kelman's constant derived from the grid system. The leading values snap to 15pt baseline multiples.

```
Font Size × 1.176 = Line Height
```

For heading contexts, use `--leading-heading: 1.176`. For body text at golden ratio, use `--leading-body: 1.618`.

### CSS Variables

```css
:root {
  --type-xs: 0.6rem;       /* ~9.6px — footnotes */
  --type-caption: 0.75rem;  /* 12px — labels, captions, mono */
  --type-label: 0.875rem;   /* 14px — card body, UI text */
  --type-body: 1.25rem;     /* 20px — main body text */
  --type-lead: 1.5rem;      /* 24px — lead paragraphs, intro */
  --type-h4: 2rem;          /* 32px — card titles, sub-sections */
  --type-h3: 2.5rem;        /* 40px — section sub-titles */
  --type-h2: 3.25rem;       /* 52px — section titles */
  --type-h1: 5.25rem;       /* 84px — display, hero */
  --type-display: 8.5rem;   /* 136px — massive display */
}
```

---

## 4. MÜLLER-BROCKMANN TYPOGRAPHY RULES

These rules come directly from *Grid Systems in Graphic Design* and must be followed:

### 4.1 Words Per Line (Measure)

> "According to a well-known empirical rule there should be 7 words per line for a text of any length."

- **Body text (--type-body at 1.25rem):** 7–10 words per line
- At 1.25rem with Söhne, this requires a column width of approximately 4–6 grid columns (33%–50%)
- **NEVER** let body text span the full 12 columns — it becomes unreadable

### 4.2 Column Width Proportioned to Type Size

> "The column must be proportioned to the size of the type."

| Type Size | Recommended Column Span | Words/Line |
|---|---|---|
| --type-caption (0.75rem) | 3–4 cols | 7–10 |
| --type-body (1.25rem) | 4–6 cols | 7–10 |
| --type-lead (1.5rem) | 5–7 cols | 7–10 |
| --type-h4+ (2rem+) | Can span wider | Display context |

### 4.3 Leading (Line Height)

> "Leading calls for just as close attention as the width of the lines."

- Too tight: "The upper and lower line are both taken in by the eye at the same time. The eye is distracted."
- Too loose: "The reader has trouble in linking up with the next line, his uncertainty grows, and fatigue sets in earlier."
- **Good leading:** "Can carry the eye optically from one line to the next, giving it confidence and stability."

### 4.4 Size Differences Must Be Unequivocal

> "If a variety of type sizes are to be used, the differences between them must be clearly recognizable."

- 9pt must be immediately distinguishable from 6pt
- Medium weight = light grey area, semi-bold = medium grey, bold = deep grey
- **Clear contrasts between typefaces AND sizes make for quick and easy reading**

### 4.5 Margins — Golden Section Proportions

> "All the famous typographic works of previous centuries have marginal proportions which have been carefully calculated using the Golden Section."

- VAREN uses asymmetric margins: 4.924% top, 12.5% bottom (gravity anchor)
- Side margins: 2.77% (35.451pt / 1280pt)
- "Margins of the same size can never result in an interesting page design; they always create an impression of indecision and dullness."

### 4.6 Body vs. Display Faces

> "If unity of typeface is desired, headings must be displayed in the same kind of face."

VAREN uses 4 typeface families, each with a clear role:

| Family | Role | Usage |
|---|---|---|
| Signifier (serif) | Editorial voice | Headlines, manifesto, narrative, quotes |
| Söhne (sans) | Functional body | UI, body text, descriptions |
| Söhne Schmal (narrow) | Drama/display | Section numbers, large headings, hero |
| Söhne Mono (mono) | Technical/data | Labels, captions, chapter markers, code |

---

## 5. HIERARCHY DECISION TREE

When setting any text element, follow this decision process:

```
1. WHAT IS THIS CONTENT?
   ├─ Display headline → Söhne Schmal, --type-h1 or --type-display, weight 600
   ├─ Section title → Signifier, --type-h2, weight 300, italic for subtitles
   ├─ Card/subsection title → Serif or Sans, --type-h4, weight 300-500
   ├─ Lead/intro paragraph → Söhne, --type-lead, weight 300
   ├─ Body text → Söhne, --type-body, weight 400
   ├─ Label/caption → Söhne Mono, --type-caption, weight 500, uppercase, letter-spacing 0.1em+
   └─ Footnote/metadata → Söhne Mono, --type-xs, weight 400

2. HOW WIDE SHOULD IT BE?
   ├─ Headline: 6–12 cols (depends on impact)
   ├─ Body: 4–8 cols (7-10 words/line rule)
   ├─ Captions: 3–4 cols
   └─ Full-width only for: labels with lines, sub-grids, tables

3. WHAT COLOR?
   ├─ Primary text: --light (#F2F0ED)
   ├─ Secondary text: rgba(242,240,237,0.72)
   ├─ Tertiary/caption: --gray (#8A8A8A)
   ├─ Accent: --gold (#C8A96E)
   └─ Muted: rgba(242,240,237,0.55)
```

---

## 6. SPACING SYSTEM (Fibonacci)

**All spacing must use these tokens.** No arbitrary values.

| Token | Value | Pixels | Usage |
|---|---|---|---|
| --sp-1 | 0.5rem | 8px | Tight: between label and value |
| --sp-2 | 0.8125rem | 13px | Small: between related items |
| --sp-3 | 1.3125rem | 21px | Medium: between paragraphs, card padding |
| --sp-4 | 2.125rem | 34px | Large: between sections within a frame |
| --sp-5 | 3.4375rem | 55px | XL: major section gaps |
| --sp-6 | 5.5625rem | 89px | 2XL: frame padding |
| --sp-7 | 9rem | 144px | 3XL: hero padding |
| --sp-8 | 14.5625rem | 233px | 4XL: massive vertical space |

Each value ≈ previous × φ (1.618). This creates naturally harmonious proportions.

---

## 7. COLOR PALETTE

| Name | Hex | Role |
|---|---|---|
| VAREN Black | #0A0A0A | Primary background |
| Dark | #111111 | Elevated surfaces |
| Carbon | #1A1A1A | Cards, panels |
| Surface | #222222 | Hover states |
| Command Gold | #C8A96E | Accent, highlights, interactive |
| Steel Gray | #8A8A8A | Secondary text, captions |
| Gray Light | #B0B0B0 | Hover text states |
| Linen White | #F2F0ED | Primary text |

---

## 8. THE KELMAN PRESENTATION LAYOUT PATTERNS

From the VAREN Digital Presentation (InDesign/PDF), these are the canonical layout patterns:

### Pattern 1: Header Left + Content Right
```
┌─── φ-A ───┬─── φ-B ───┬─── φ-C ───┬─── φ-D ───┐
│            │            │  Header    │  Body text │
│  Large     │            │  Medium    │  (smaller) │
│  Header    │            │  Black     │            │
│            │            │            │  • Bullets  │
│            │            │  Text body │  • Bullets  │
│            │            │  (prose)   │  • Bullets  │
└───────────┴───────────┴───────────┴───────────┘
```

### Pattern 2: Title + Two-Column Body
```
┌─── φ-A ───┬─── φ-B ───┬─── φ-C ───┬─── φ-D ───┐
│  Title     │            │            │            │
│  Large     │            │            │            │
│            │            │            │            │
│  Body Col1 │  Body Col2 │            │            │
│  (prose)   │  (prose)   │            │            │
│            │            │            │            │
└───────────┴───────────┴───────────┴───────────┘
```

### Pattern 3: Grid of Cards/Boxes
```
┌─── φ-A ───┬─── φ-B ───┬─── φ-C ───┬─── φ-D ───┐
│  [box]     │  [box]     │  [box]     │  [box]     │
│            │            │            │            │
│  [box]     │  [box]     │  [box]     │  [box]     │
│            │            │            │            │
└───────────┴───────────┴───────────┴───────────┘
```

---

## 9. ABSOLUTE RULES

1. **All type sizes must come from the type scale.** No arbitrary sizes.
2. **All spacing must use Fibonacci tokens.** No arbitrary margins/padding.
3. **All leading must maintain the 1.176× ratio** or snap to the 15px baseline.
4. **Content must align to the 12-column grid.** Elements snap to column boundaries.
5. **Body text: 7–10 words per line.** Never wider than 8 columns for prose.
6. **Section frames target 16:9 aspect ratio** with asymmetric top/bottom margins.
7. **Weight changes must be intentional.** Each weight shift signals hierarchy change.
8. **No rotation transforms on cards.** Cards must be straight, aligned, precise.
9. **Fewer size differences = quieter, more professional design.** (Müller-Brockmann)
10. **The grid is the authority.** If it doesn't fit the grid, it doesn't ship.

---

## 10. REFERENCE DOCUMENTS

| Document | Location | Purpose |
|---|---|---|
| Grid Systems in Graphic Design (Müller-Brockmann) | Resources/Grid systems.pdf | Typography, column width, leading, margins |
| VAREN Digital Presentation Grid System | uploads/VAREN Digital Presentation Landscape Grid System.pdf | Kelman 4-column modular grid, exact measurements |
| Kelman InDesign Source | uploads/Digital Presentation Landscape Grid System v2.idml | Original grid construction |
| VAREN Brand Bible | VAREN_Brand_Bible.docx | Brand voice, messaging, positioning |
| VAREN Strategic Landscape Report | VAREN_Strategic_Landscape_Report.docx | Market positioning, competitor analysis |
| VAREN Logo Kit | VAREN® Logo Kit mk1/ | All logo variations, styleguide |
| Widescreen Illustrator File | uploads/Widescreen 1280x720 002.ai | Proportional layout reference |

---

*This instruction set is derived from the golden ratio (φ = 1.618), Müller-Brockmann's Swiss typographic tradition, and Stephen Kelman's digital adaptation. It is the single source of truth for all design decisions on the VAREN Brand Experience.*
