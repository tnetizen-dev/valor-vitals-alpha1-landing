# Claude Code Brief: Valor Vitals Alpha 1 Landing Page

## The Assignment

Build a high-conversion product landing page for the **Valor Vitals Alpha 1 Enhanced Multivitamin**. This is a static HTML/CSS/JS page (no framework required) that will serve as the primary front-end offer page driven by Meta ad traffic.

The page is modeled on two references:
- **Jocko Fuel** — for visual identity: dark, tactical, high-contrast, no fluff
- **Hydrant** — for functional architecture: clean buy box, quantified social proof, clear subscription framing

Your two primary documents for this build are in this folder:

- **`PRD-alpha1-landing-page.md`** — the full product requirements document. Read this first. It defines every section of the page, the visual system, conversion requirements, and brand voice constraints.
- **`copy-alpha1-landing-page.md`** — the complete copy for every section of the page. Use this as the source of truth for all text. Do not write your own copy — pull directly from this file.

---

## Folder Structure

All files are inside the root `Valor Vitals/` folder. Paths below are relative to that root.

```
Valor Vitals/
├── product-landing-page/              ← You are here. Build the landing page output here.
│   ├── CLAUDE-CODE-BRIEF.md           ← This file
│   ├── PRD-alpha1-landing-page.md     ← Full requirements — read first
│   └── copy-alpha1-landing-page.md    ← All page copy — use verbatim
│
├── core/
│   ├── brand-source-of-truth.md      ← Brand positioning, customer motivations, messaging themes
│   ├── brand-voice.md                ← Voice rules, vocabulary, things to avoid — read before writing anything
│   ├── offers.md                     ← Product details, pricing, ingredient specs
│   ├── persona.md                    ← Customer personas (The Operator, The Protector, etc.)
│   └── ad-scripts-callon-v1.md       ← Callon's original UGC ad scripts — the voice comes from here
│
└── media/
    ├── Product and brand images/
    │   ├── VALORVITALS-Multivitamin-Front (1).png   ← Primary product image (use in hero + buy box)
    │   ├── VALORVITALS-Multivitamin-Back.png         ← Back of bottle (supplement facts)
    │   ├── VALORVITALS-Multivitamin-Side.png         ← Side of bottle
    │   ├── VALORVITALS-Multivitamin-Hydration Bundle.png  ← Bundle image (reference only for now)
    │   └── ValorVitals-LogoLockups.pdf               ← Brand logos — extract the appropriate lockup
    │
    └── Callon USMC images/                           ← Authentic founder/lifestyle photos
        ├── IMG_0015.JPG
        ├── IMG_0171.jpg
        ├── Promotion.webp
        ├── Screenshot 2026-04-16 at 11.55.11 PM.png
        └── [additional numbered JPGs]                ← Review all; select the strongest for hero/testimonial sections
```

---

## Build Specifications

### Output
- Single `index.html` file with embedded CSS (and JS where needed for interactivity)
- Save output to: `product-landing-page/index.html`
- Mobile-first. The buy box must be fully visible without scrolling on a standard mobile viewport (375px width).

### Visual System
- **Background:** Charcoal / dark slate (#1a1a1a or similar)
- **Text:** White / off-white for primary; light grey for secondary
- **Accent:** Safety Orange (#FF6B00 or similar) — used sparingly for CTAs, key data points, and the specs bar
- **Typography:** System sans-serif stack with heavy weights (font-weight: 800–900 for headlines). If loading a web font, use a bold condensed sans — something in the spirit of Bebas Neue or Barlow Condensed.
- **Imagery style:** Raw, real, unpolished. No studio lighting, no stock photo energy.

### Page Sections (in order)

1. **Hero** — Full-width, headline over a lifestyle image. CTA button.
2. **Buy Box** — Specs bar, product image, purchase toggle (one-time / subscription), CTA, social proof numbers below.
3. **Readiness Equation** — Visual formula display.
4. **Field Reports (Testimonials)** — 4-card grid, one per persona.
5. **Ingredient Cards** — Dark-mode data sheet cards, one per key ingredient.
6. **Body as Gear** — Full-width text section with headline and body copy.
7. **30-Day Guarantee** — Simple, clean callout.
8. **Collapsible Technicals** — Accordion for Supplement Facts and Usage Instructions.
9. **Footer** — Tagline + copyright.

### Conversion Requirements (non-negotiable)
- Subscribe & Save option must be **pre-selected** by default on page load
- The subscription option must be labeled **"Maintenance Protocol"**
- Benefits (10% Savings / Free Shipping / 30-Day Readiness Guarantee) must be visible on the toggle itself — not hidden in fine print
- Primary CTA copy: **"Start Your Protocol"**
- Supplement Facts and Usage Instructions must be in **collapsible/accordion sections** — not open by default
- Social proof bar (customer count / capsules shipped) uses **placeholder numbers** — format as `[X,XXX] Customers | [X,XXX,XXX] Capsules Shipped` until real data is supplied

### Brand Voice Constraints
These apply to any text you write (labels, micro-copy, error states, etc.):
- **No exclamation points — anywhere on the page**
- **No hype words:** no "supercharge," "dominate," "maximize," "biohack," "game-changer," "transformation," "best self"
- **Tone:** calm, direct, peer-to-peer. Read `core/brand-voice.md` before writing any micro-copy.

### Known Flag to Resolve
The Lion's Mane dosage appears as **600mg** in the PRD and copy doc, but **300mg** in `core/offers.md`. All instances in `copy-alpha1-landing-page.md` are marked `[LION'S MANE DOSE]`. Before rendering this value on the page, confirm the correct dosage. Use whichever number you're instructed to use, but do not guess.

---

## What Good Looks Like

- The page should feel like it was built by someone who has actually been in a field environment — not a wellness brand, not a gym supplement company.
- Visual weight comes from typography and contrast, not decoration.
- Every data point on the page is specific and earned — no vague claims.
- The buy box is the center of gravity. Everything else on the page supports the decision to buy.

When in doubt, refer to `core/brand-voice.md` for tone and `PRD-alpha1-landing-page.md` for structure. The copy doc is the final word on all text.
