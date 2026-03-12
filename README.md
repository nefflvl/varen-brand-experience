# VAREN® Brand Experience

Brand narrative and identity system for VAREN — elite performance golf.

**Production:** [varen-brand-experience.pages.dev](https://varen-brand-experience.pages.dev)

## Branching Model

| Branch | Purpose | Deploys To |
|--------|---------|------------|
| `main` | Production | `varen-brand-experience.pages.dev` |
| `develop` | Staging / Preview | `develop.varen-brand-experience.pages.dev` |
| `feature/*` | Isolated work | `feature-*.varen-brand-experience.pages.dev` |

## Workflow

```
feature/brand-experience-preview → develop → main
        (work here)                (staging)  (production)
```

## Stack

- **Typography**: Signifier (serif) · DM Sans (sans-serif) · DM Mono (monospace)
- **Grid**: Swiss 12-column modular grid, golden ratio (φ = 1.618) type scale
- **Spacing**: Fibonacci scale (8, 13, 21, 34, 55, 89, 144, 233px)
- **Logo System**: VAREN® Logo Kit mk1 — Half-Y, Thirds, Vertical Golden Ratio, Insignia
- **Deployment**: Cloudflare Pages — static, no build step
