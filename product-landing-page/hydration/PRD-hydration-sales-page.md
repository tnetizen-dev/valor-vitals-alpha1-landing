# PRD: Valor Vitals Hydration Long-Form Sales Page

**Version:** 1.0 — 2026-08-26
**Format:** Single-column long-form sales page (advertorial), cold Meta traffic
**Strategy source:** `sales page copy/2026-08-25-longform-page-strategy.md` · `offer/2026-08-25-hydration-offer-structure-and-game-plan.md`

---

## 1. What this page is for

One job: convert a stranger who is tired at 2pm into a first-time buyer of a $29 bag of hydration sticks.

It is **not** trying to sell the A1, build a brand, or explain the full product line. The A1 arrives later, in the post-purchase flow and by email. Anything on this page that isn't moving someone toward the $29 is cut.

**Audience:** men, roughly 30–55, who work long physical or high-stress days — trades, first responders, shift workers, active civilians. They already drink water. They already own an electrolyte product. They have mis-diagnosed the afternoon wall as age.

---

## 2. Visual system

### The core departure

The A1 landing page is dark, tactical, high-contrast — modelled on Jocko Fuel. **This page is not.** Two thousand words of reversed-out type does not get read, and readability is the only reason to choose this format. Brand identity here is carried by the logo, the accent colour, the product photography, and the voice.

### Tokens

| Token | Value | Use |
|---|---|---|
| `--ground` | `#FBFAF8` | Page background. Warm off-white, not pure white |
| `--ink` | `#1A1D1C` | Body copy |
| `--ink-2` | `#4A4F4C` | Secondary text, captions |
| `--accent` | Pull the primary from `media/valor_vitals_logo.png` | CTAs, rules, emphasis |
| `--accent-ink` | Whatever reads at 4.5:1 on `--accent` | CTA label |
| `--panel` | `#F1EFEA` | Section grounds, comparison table |
| `--success` | Desaturated green | Comparison table checkmarks |

Dark mode is **out of scope** — this is an ad landing page with a controlled context, and a second theme is surface area for bugs that nobody will see. Set colours explicitly so the page holds regardless of user agent.

### Type

- **Headings:** a sturdy grotesque or slab. Weight and tightness carry the tone; do not use a display face with personality of its own.
- **Body:** a highly readable serif or humanist sans at **17px minimum on mobile**, 19px desktop. Line height 1.6. Measure 40–80 characters.
- One `h1` (the hero headline). Section headings are `h2`. Never skip a level.
- New paragraph every 3–4 lines. A subheading every 2–3 paragraphs. Long paragraphs are the failure mode of this format.

### Rhythm

Alternate the visual treatment every 2–3 sections — full-bleed photo, plain text, panelled block, pull quote — so the page doesn't read as an undifferentiated wall. Novelty sustains attention; monotony ends the session.

---

## 3. Section order and scroll targets

Depth percentages are targets for the **built page at 375px**, and they are requirements, not suggestions. Verify them after build.

| # | ID | Section | Depth | Copy key |
|---|---|---|---|---|
| 1 | `hero` | Hero | 0% | `S1_HERO` |
| 2 | `trust` | Trust ribbon | ~3% | `S2_TRUST` |
| 3 | `problem` | Problem agitation | 5–18% | `S3_PROBLEM` |
| 4 | `mechanism` | **Palatinose reveal** | 18–24% | `S4_MECHANISM` |
| 5 | `cta-1` | **Buy button 1 + sticky bar activates** | **24%** | `CTA_PRIMARY` |
| 6 | `founder` | Founder credibility | 26–36% | `S5_FOUNDER` |
| 7 | `cta-2` | Buy button 2 | 36% | `CTA_PRIMARY` |
| 8 | `panel` | Ingredient comparison | 38–48% | `S6_PANEL` |
| 9 | `transformation` | Before / after | 48–56% | `S7_TRANSFORMATION` |
| 10 | `cta-3` | Buy button 3 | 56% | `CTA_PRIMARY` |
| 11 | `offer` | Offer and price | 58–68% | `S8_OFFER` |
| 12 | `cta-4` | **Buy button 4 — inline offer module** | 68% | `S9_STACK` |
| 13 | `guarantee` | The guarantee | 70–80% | `S10_GUARANTEE` |
| 14 | `cta-5` | Buy button 5 | 80% | `CTA_PRIMARY` |
| 15 | `faq` | FAQ | 82–92% | `S11_FAQ` |
| 16 | `close` | Close | 92–97% | `S12_CLOSE` |
| 17 | `cta-6` | Buy button 6 — final | 97% | `CTA_PRIMARY` |

**Nothing renders after `cta-6`** except a minimal legal footer. The ConversionWise audit flagged exactly this on the A1 page: it ended on a CTA and then restarted with more education, and "it reads like the page ran out and then started again."

### Why no buy button in the hero

Two reasons, and they pull the same direction. A visitor who hasn't yet accepted they have a problem will not click a buy button — the ask lands on nobody. And a hard sell in the first screen of an editorial page tells cold traffic this is an ad, which costs the read that the whole format depends on.

The hero instead carries the **price, stated plainly**, and a scroll cue. Price transparency up front removes the "how much is this going to be" tax without spending the ask.

---

## 4. Interaction spec

This is the part the A1 build didn't have. It is the highest-leverage section of this document.

### 4.1 The buy drawer

Every in-body buy button (`cta-1`, `2`, `3`, `5`, `6`) opens a drawer that slides up from the bottom of the viewport over a scrim. **It must not scroll the page.**

The evidence: on a supplement store at 3,000+ conversions per variation, a mobile sticky button that scrolled the reader to the buy area produced +6% add-to-cart clicks and **no statistically significant difference in orders**. The drawer variant produced +11.8% clicks and **+5.2% orders at 98% significance**. Moving the reader is what costs you.

**Drawer contents, in order:**

1. Product image thumbnail (gusset bag)
2. Flavour selector — B1 Blue Raspberry / B2 Lemon Lime. **Required.** No default selected; the CTA is disabled until one is chosen
3. Price line: `$29` with `$44.99` struck through beside it, and the label `first bag`
4. **The second-flavour upgrade**, as a distinct row:
   - Label: `Add the other flavour — $19`
   - Sub-label: `Same box. No extra shipping.`
   - **Unchecked by default.** Do not pre-select this. It is an easy yes, not a default someone fails to notice, and this brand cannot pre-tick an upsell
   - When checked, the total updates to `$48` with visible feedback
5. Guarantee line: `Use the whole bag. If three o'clock isn't different, keep it and we'll refund you.`
6. Primary action: `Add to cart — $29` (label reflects live total)

**Behaviour:**
- Opens on button click; scrim click, Escape, and an explicit close control all dismiss it
- Focus moves to the drawer on open, is trapped while open, returns to the triggering button on close
- Page scroll locks while open, and the scroll position is preserved exactly on close
- Slide-up animation ~250ms, disabled under `prefers-reduced-motion`
- Submits to Shopify cart and proceeds **straight to checkout**. Skip the cart page — this is a single-product page with nothing to cross-sell there

### 4.2 The sticky bar

- **Hidden until the user scrolls past `cta-1`.** Not visible at page load. Showing it immediately burns the ask before conviction and reads as an ad on an editorial page
- Once shown, persists for the remainder of the page
- Hidden while the drawer is open
- Contents: product name, `$29`, and a button. Compact — one line on mobile
- Clicking it opens the same drawer
- Respects safe-area insets on iOS

### 4.3 The inline offer module (`cta-4`)

The single place the buy interface renders inline rather than as a drawer, because at 68% depth the reader has earned a full look at what they're getting.

Contains the flavour selector, the value stack table (`S9_STACK`), the second-flavour upgrade row, the guarantee, and the primary action. Same submit behaviour as the drawer.

### 4.4 FAQ accordion

Native `<details>`/`<summary>`. First item open by default, rest closed. Each open emits an event (see `analytics-events.md`) — which question people open is genuinely useful information at this traffic volume.

---

## 5. The comparison table (`S6_PANEL`)

**This is the highest-leverage asset on the page.** Build it as a real table, not an image — it must be readable at 375px and selectable by screen readers.

- Rows: sodium, potassium, magnesium, slow-release carbohydrate, added cane sugar, artificial dyes, stimulants
- Columns: **Valor Vitals** | Leading zero-sugar stick | Leading tablet | Leading sugar stick
- **Never name a competitor.** Generic descriptors only. This was a decision made on 24 Aug, not an oversight
- Valor's column gets the accent treatment; competitor columns stay neutral
- Where a competitor has a zero or a gap, show it as a visible absence rather than a dash lost in a grid — the whole argument is "every one of them has a hole in the panel somewhere"
- Horizontal scroll inside its own `overflow-x: auto` container. The page body must never scroll sideways

⚠️ **Every number in this table traces to `email/Payday Resupply — Broadcast Email + SMS 2026-07-31.md` and needs confirming against a photo of the actual B1/B2 panel before this page goes live.** Competitor figures need sourcing too. Build it; don't launch it unverified.

---

## 6. Brand voice constraints

Read `core/brand-voice.md` and `memory/glossary.md` in full. The load-bearing ones for this page:

- **Callon is a Marine Corps officer** — never "infantry." Name spelled C-A-L-L-O-N, always.
- **EMT-certified**, never implied to have worked as an EMT running calls.
- **Andrew: "spent over a decade in the SEAL teams."** Exact wording. Never name a unit.
- **Callon is not a firefighter** and claims no proximity he doesn't have.
- **No manufactured urgency.** No countdown timers, no fake stock counters, no "3 people are viewing this."
- **No exclamation points.** Calm and measured is the voice.
- The founder credential validates the **product**, never claims membership in the customer's tribe.

⚠️ **Open compliance item:** whether outcome copy carries the DSHEA disclaimer sitewide has not been decided. Until it is, phrase after-state copy as lived experience rather than product action, and leave a footer slot for the disclaimer.

---

## 7. Technical requirements

- Meta Pixel + CAPI on this page, with its own custom conversion distinct from the A1 page's Purchase event. The two campaigns must not optimise against each other
- Microsoft Clarity installed from day one
- Every event in `analytics-events.md` fires
- Canonical URL set; page excluded from sitemap and marked `noindex`. **The $29 must never be discoverable from the main site** — the $44.99 anchor has to survive
- No external font hosts, no CDN scripts, no third-party embeds beyond pixel and Clarity

---

## 8. Out of scope for v1

Reviews and testimonials (no volume yet), video (add once footage exists — CXL cites above-fold video tests at +46% and +25% sales, so this is a v2 priority), subscription option on this page (the ascension happens post-purchase), A1 cross-sell anywhere on the page.
