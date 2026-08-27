# Claude Code Brief: Valor Vitals Hydration Long-Form Sales Page

## The Assignment

Build a **single-column long-form sales page** for Valor Vitals Hydration (B1 Blue Raspberry / B2 Lemon Lime). Static HTML/CSS/JS, no framework. This is a cold-traffic acquisition page driven by Meta ads — it is **not** a PDP.

**This is a different kind of page from the A1 landing page in the parent folder.** That page is a product page with a buy box. This one is an argument that happens to end in a purchase, several times over. Do not model it on `../index.html`.

### Read these first, in this order

| File | What it is |
|---|---|
| `PRD-hydration-sales-page.md` | **Read first.** Full requirements: section order, scroll-depth targets, CTA positions, interaction spec, visual system |
| `copy-hydration-sales-page.md` | **All page copy. Use verbatim.** Do not write your own copy. Every section is keyed to a PRD section ID |
| `assets-manifest.md` | Which image goes in which section, and which assets don't exist yet |
| `analytics-events.md` | Events the page must emit. Not optional — the page cannot be evaluated without them |
| `../../core/brand-voice.md` | Voice guardrails. Read before writing any string not in the copy file (button labels, alt text, error states) |
| `../../memory/glossary.md` | Founder credential boundaries and the Authenticity Rule. Non-negotiable |

---

## The one thing that matters most

Valor's own Clarity data, last 30 days: **88% of sessions are mobile**, and only **28% of mobile sessions reach 25% scroll depth.** 11% reach 75%. 4% reach the bottom.

Every structural decision in the PRD follows from that. In particular:

- The **first buy button sits at roughly 24% page depth**, immediately after the palatinose mechanism reveal — not at the bottom, and not in the hero.
- A **sticky bottom bar activates at that first button** and persists for the rest of the page.
- Buttons open a **buy drawer in place**. They must never anchor-scroll the reader to a different part of the page.

If you find yourself moving a CTA lower "because the argument isn't finished yet," stop and re-read this section.

---

## Folder Structure

```
Valor Vitals/
├── product-landing-page/
│   ├── index.html                          ← A1 page. Reference only. Different format.
│   └── hydration/                          ← YOU ARE HERE. Build output goes here.
│       ├── CLAUDE-CODE-BRIEF-hydration.md  ← This file
│       ├── PRD-hydration-sales-page.md     ← Requirements — read first
│       ├── copy-hydration-sales-page.md    ← All copy — verbatim
│       ├── assets-manifest.md              ← Image mapping + gaps
│       ├── analytics-events.md             ← Event spec
│       └── index.html                      ← BUILD THIS
│
├── core/
│   ├── brand-voice.md                      ← Voice rules
│   ├── offers.md                           ← Product and pricing detail
│   └── persona.md                          ← Marcus and Ryan
│
├── memory/glossary.md                      ← Credential boundaries, Authenticity Rule
│
└── media/Product and brand images/hydration packs/   ← Product renders
    media/Callon USMC images/                          ← Founder photos
    media/Lifestyle Photos/ + media/vv lifestyle photos/
```

---

## Build Specifications

### Output
- **Single `index.html`** in this folder, with embedded CSS and JS. No build step, no external dependencies, no CDN links.
- **Mobile-first.** Design at 375px, enhance upward. 88% of traffic is mobile — desktop is the secondary case, not the primary one.
- Images referenced by relative path from `media/`. Do not inline large images as data URIs.

### Non-negotiables
1. **Single column throughout.** No side-by-side content blocks on mobile. The comparison table is the only element allowed to scroll horizontally, inside its own container.
2. **Dark text on a light ground.** This is a deliberate departure from the A1 page's dark tactical treatment — 2,000+ words of reversed-out type does not get read. Brand identity is carried by the logo, the accent colour, and the product photography, not by a dark background.
3. **Body copy 17px minimum on mobile**, line length 40–80 characters, generous line height. Readability is the format's entire advantage.
4. **No AI-generated humans, uniforms, gear, apparatus or station environments.** The Authenticity Rule in `memory/glossary.md` is absolute. If a needed image doesn't exist, leave a clearly marked placeholder and flag it — never generate one.
5. **The page emits every event in `analytics-events.md`.** Build them in as you go. Retrofitting them is how they end up not happening.

### Performance
- Target LCP under 2.5s on a mid-range mobile device on 4G. The hero image is the LCP element — size it properly and set `fetchpriority="high"`.
- Everything below the first viewport gets `loading="lazy"`.
- Total page weight under 1.5MB including images.

### Accessibility
- Semantic landmarks, one `h1`, heading levels in order.
- The buy drawer is a real dialog: focus moves into it on open, focus is trapped while open, Escape closes it, focus returns to the button that opened it.
- Visible focus states on every interactive element. Respect `prefers-reduced-motion`.
- Colour contrast 4.5:1 minimum on body text.

---

## What NOT to do

- **Don't write copy.** Every word comes from `copy-hydration-sales-page.md`. If something is missing, flag it rather than filling the gap.
- **Don't add sections.** No "as seen in" strip, no review carousel, no countdown timer, no exit-intent popup. The brand voice explicitly forbids manufactured urgency and this audience punishes it.
- **Don't put a buy button in the hero.** This is deliberate and it is explained in the PRD.
- **Don't anchor-scroll on CTA click.** Tested, and it produces more clicks and no more orders.
- **Don't name a competitor.** The comparison is generic — "the leading zero-sugar stick." This was a decision, not an oversight.
- **Don't use localStorage or sessionStorage** for anything the purchase depends on.

---

## Definition of done

- [ ] Renders correctly at 375px, 768px, 1440px
- [ ] First buy button falls between 20% and 28% of total page height on a 375px viewport
- [ ] Six buy buttons, at the depths specified in the PRD
- [ ] Sticky bar appears at button 1 and not before
- [ ] Drawer opens, traps focus, closes on Escape, returns focus
- [ ] Every event in `analytics-events.md` fires and is visible in the console in debug mode
- [ ] No console errors
- [ ] Every image has meaningful alt text
- [ ] Placeholder assets are visually obvious and listed in a comment block at the top of the file
