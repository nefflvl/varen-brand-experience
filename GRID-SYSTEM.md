# VAREN® Harmonic Grid System

## Source: VAREN Digital Presentation Landscape Grid System (1280 × 720)

All measurements derived from φ (golden ratio) relationships applied to the 16:9 canvas.
Every design decision on this site must conform to this grid system.

## Algorithm: The VAREN Harmonic Grid™

Every measurement in this system traces back to φ (1.618):

- **Canvas**: 1280 × 720pt — 16:9 aspect ≈ φ² (2.618 ≈ 2.56)
- **Margins**: 720 / φ⁴ / 3 = 35.451pt (side/top) — bottom: 90pt (6× baseline, asymmetric gravity)
- **Gutters**: baseline × φ⁻² = 15 × 1.3634 ≈ 20.451pt
- **Baseline**: φ × 9.27 ≈ 15pt
- **Type scale**: Musical harmonic intervals — ×1.333 (perfect 4th) alternating with ×1.5 (perfect 5th)
- **Leading**: Constant 1.176× ratio — all values snap to 15pt baseline multiples
- **Spacing**: Fibonacci sequence (each ≈ previous × φ) — 8, 13, 21, 34, 55, 89, 144, 233px
- **Columns**: 4 φ-macro × 3 Swiss micro = 12-column modular grid

---

## Document Specifications

| Property | Value | Web Equivalent |
|----------|-------|----------------|
| Page Size | 1280 × 720pt | 16:9 aspect ratio |
| Intent | WebIntent | Viewport-based layout |
| Orientation | Landscape | Horizontal frames |

## Column Grid (Vertical)

| Property | IDML Value | CSS Value |
|----------|-----------|-----------|
| Columns | 4 | `grid-template-columns: repeat(4, 1fr)` |
| Gutter | 20.451pt | `1.28rem` (1.598% of width) |
| Left Margin | 35.451pt | `2.77%` / `clamp(2.2rem, 5vw, 5.5rem)` |
| Right Margin | 35.451pt | `2.77%` / `clamp(2.2rem, 5vw, 5.5rem)` |
| Top Margin | 35.451pt | `4.924%` of height |
| Bottom Margin | 90pt | `12.5%` of height (asymmetric) |

### Column Positions (from IDML)

```
Col 1 start:   0pt        →  0%
Col 1 end:     286.936pt  →  22.42%
Gutter 1:      307.387pt  →  24.01%
Col 2 start:   307.387pt  →  24.01%
Col 2 end:     594.324pt  →  46.43%
Gutter 2:      614.775pt  →  48.03%
Col 3 start:   614.775pt  →  48.03%
Col 3 end:     901.711pt  →  70.45%
Gutter 3:      922.162pt  →  72.04%
Col 4 start:   922.162pt  →  72.04%
Col 4 end:     1209.098pt →  94.46%
```

Content width: 1209.098pt (94.46% of page width)

## Baseline Grid (Horizontal)

| Property | Value | Web Equivalent |
|----------|-------|----------------|
| Division | 15pt | `0.9375rem` / `15px` |
| Start | 0 (top of page) | `0` |
| Content rows | 39 full rows | Within margins |
| Content height | 594.549pt | `720 - 35.451 - 90` |

### Row Positions (within content area)

At 15pt intervals from top margin (35.451pt):
- Row 1: 35.451pt → Row 2: 50.451pt → Row 3: 65.451pt → ...
- Row 39: 605.451pt (last full row before bottom margin at 630pt)

In CSS: `background-size: 100% 15px` with repeating gradient.

## 16:9 Frame System

Each section ("frame") targets the 16:9 viewport ratio:

```css
.frame {
  min-height: 100vh;
  position: relative;
  padding-top: 4.924vh;     /* VAREN Harmonic top margin: 35.451/720 */
  padding-bottom: 12.5vh;   /* VAREN Harmonic bottom margin: 90/720 */
  padding-left: 2.77vw;     /* VAREN Harmonic left margin: 35.451/1280 */
  padding-right: 2.77vw;    /* VAREN Harmonic right margin: 35.451/1280 */
}
```

The asymmetric bottom margin (12.5% vs 4.924% top) creates visual weight at the bottom of each frame, anchoring content upward — a deliberate Swiss typographic convention.

## Type Scale

Derived from VAREN Harmonic IDML paragraph styles.

| Step | Size (pt) | Leading (pt) | Ratio | Leading/Size | CSS rem |
|------|-----------|--------------|-------|-------------|---------|
| 1 | 68 | 80 | — | 1.176 | 5.25rem |
| 2 | 59.5 | 70 | ÷1.143 | 1.176 | 4.59rem |
| 3 | 51 | 60 | ÷1.167 | 1.176 | 3.94rem |
| 4 | 38.25 | 45 | ÷1.333 | 1.176 | 2.95rem |
| 5 | 25.5 | 30 | ÷1.5 | 1.176 | 1.97rem |
| 6 | 19.125 | 22.5 | ÷1.333 | 1.176 | 1.48rem |
| 7 | 12.75 | 15 | ÷1.5 | 1.176 | 0.98rem |
| 8 | 9.5625 | 11.25 | ÷1.333 | 1.176 | 0.74rem |

### Key Relationships

- **Leading ratio**: Constant 1.176× (size × 1.176 = leading)
- **Scale intervals**: Alternating ×1.333 (perfect 4th) and ×1.5 (perfect 5th)
- **Musical intervals**: The type scale follows harmonic musical proportions
- **Baseline snap**: All leading values are multiples of 15pt (the baseline grid)

## Type Families

| Role | Family | Weights Used |
|------|--------|-------------|
| Editorial serif | Signifier (Klim) | Thin (100) through Black (900) |
| Functional sans | Söhne (Klim) | Extraleicht (200) through Extrafett (900) |
| Display narrow | Söhne Schmal (Klim) | Leicht (300) through Extrafett (900) |
| Technical mono | Söhne Mono (Klim) | Leicht (300) through Dreiviertelfett (700) |

### Weight Mapping (German → CSS)

| German | CSS font-weight |
|--------|----------------|
| extraleicht | 200 |
| leicht | 300 |
| buch | 400 |
| kräftig | 500 |
| halbfett | 600 |
| dreiviertelfett | 700 |
| fett | 800 |
| extrafett | 900 |
| kursiv | italic |
| schmal | narrow (Söhne Schmal) |
| breit | wide (Söhne Breit) |

## Spacing System (Fibonacci)

| Token | Value | px |
|-------|-------|----|
| --sp-1 | 0.5rem | 8 |
| --sp-2 | 0.8125rem | 13 |
| --sp-3 | 1.3125rem | 21 |
| --sp-4 | 2.125rem | 34 |
| --sp-5 | 3.4375rem | 55 |
| --sp-6 | 5.5625rem | 89 |
| --sp-7 | 9rem | 144 |
| --sp-8 | 14.5625rem | 233 |

All spacing values are Fibonacci numbers in pixels. This creates naturally harmonious proportions that relate to the golden ratio (φ = 1.618).

## Grid Overlay

The site includes a toggleable grid overlay (bottom-right "Grid" button) that displays:

1. **4 vertical columns** with gutter gaps — matching the VAREN Harmonic column positions
2. **15px horizontal baseline rows** — repeating across the full viewport

The overlay is purely visual and does not affect layout. It exists for design verification during development.

## Rules

1. **All type sizes must come from the type scale.** No arbitrary sizes.
2. **All spacing must use Fibonacci tokens.** No arbitrary margins/padding.
3. **All leading must maintain the 1.176× ratio** or snap to the 15px baseline.
4. **Content must align to the 4-column grid.** Elements span 1, 2, 3, or 4 columns.
5. **Section frames target 16:9 aspect ratio** with asymmetric top/bottom margins.
6. **Weight changes must be intentional.** Each weight shift signals hierarchy change.
7. **The grid is the authority.** If it doesn't fit the grid, it doesn't ship.
