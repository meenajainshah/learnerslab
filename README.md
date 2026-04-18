# Learners Lab

A discovery layer for programs, workshops and summer camps. Helping Ahmedabad parents find the right experiences for their children — without combing through PDFs.

## Context & Why

- **Type**: Feature — unifying VASCSC and INME (previously two separate one-off pages) into a single Learners Lab site
- **Reason**: Two separate Vercel deployments with shared branding isn't a product. This is the v1 structure that makes it a proper discovery platform
- **How it helps**: Parents get one URL (`learnerslab.in`) and can cross-navigate between providers. Each new provider is just a new folder. Scales cleanly.
- **Status**: Live

## Structure

```
learners-lab/
├── index.html          → /         (home — lists all providers)
├── inme/
│   └── index.html      → /inme     (INME Spring & Summer 2026)
├── vascsc/
│   └── index.html      → /vascsc   (VASCSC Summer 2026 — drop in from existing)
└── vercel.json         (clean URL routing)
```

Vercel serves each folder's `index.html` at its folder path automatically. No routing config needed beyond `cleanUrls`.

## Deploy

```bash
# First time
vercel --prod

# Subsequent deploys (auto on push if connected to GitHub)
git push
```

## Adding a new provider

1. Create a new folder, e.g. `artjamming/`
2. Drop an `index.html` inside using the same design system (see `inme/index.html` as reference)
3. Add a new `<a href="/artjamming" class="provider">` card to the home page's `.providers` grid
4. Push

## Design system (consistent across all pages)

- **Background**: `#f5f2ee` (cream)
- **Text**: `#1a1a1a` (ink)
- **Accent / CTA**: `#c94a1a` (rust)
- **Secondary accent**: `#1f3d2f` (forest) for dark sections, `#e8b84a` (sun) for highlights
- **Display font**: Instrument Serif (italic for emphasis)
- **Body**: DM Sans
- **Mono / meta**: DM Mono

## Branding rules

Every page has:
- Top bar with brand dot + "Learners Lab" linking to `/`
- Top bar right-side meta with provider + season (e.g. "INME · Spring & Summer 2026")
- Footer with cross-links to home + other providers
- "Built with iView Labs" at the bottom

## Principles (for content decisions)

1. **Discovery, not registration** — every program links out to the provider. We don't handle bookings.
2. **Honest about logistics** — if a camp needs a flight from Ahmedabad, we say so.
3. **Age + interest + date + location** are the universal filters. Each provider page uses whichever subset matches its data.

---

Built with iView Labs.
