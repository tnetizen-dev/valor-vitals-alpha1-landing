# PRD: Valor Vitals Hydration Long-Form Sales Page

**Version:** 4.0 — 2026-09-03
**Format:** Single-column long-form sales page, cold Meta traffic
**Copy:** `copy-hydration-sales-page.md` v4.1 — Callon's accepted review edits plus the 3 Sep price decision
**Prior versions:** `_superseded/PRD-v3-archive.md`, `_superseded/PRD-v2-archive.md`

> **v3 replaced the copy entirely.** The page was rewritten in EGC rather than edited, and it is roughly half the length of v2. Section IDs have changed. If you are coming from the v2 build, read §3 before touching anything — most of the old IDs no longer exist.

---

## 0. What changed in v4 — read this before anything else

Two changes, and one of them will look like a mistake if you don't read this section first.

### 0.1 🚫 There is no comparison table. Do not build one.

**`S5_COMPARE` renders as prose only.** No table element, no grid, no side-by-side columns, no "vs" graphic, no placeholder for one later.

This will feel wrong while you build it, because the section is called "Put the Labels Next to Each Other" and it says *"Look at the numbers."* Those numbers are **our own supplement-facts panels, which sit immediately above it in `S4_FORMULA`**, and the invitation is for the reader to go read the back of whatever they already own. The comparison happens in their kitchen, not on the page. That is the design.

It is a decision, made twice. Competitor figures were never sourced from current labels, so the table was cut from launch scope on 3 Sep; Callon then reviewed the table-less section in his copy pass, kept it, and Tracy accepted — which makes the cut **permanent, not deferred**. Full reasoning in §5.

**What this means for the build:**

- The horizontal-scroll container in §2 has nothing to contain. No element on this page scrolls horizontally.
- `S4_FORMULA` carries two supplement-facts panel images (`[IMAGE:]` slots in the copy, paths in `assets-manifest.md`). **These are load-bearing.** They are the proof the comparison section points at. Ship them legible at 375px and tappable to zoom. A blurry panel breaks the argument two sections later.
- `section_view_compare` still fires. The section still exists; it just has no table in it.
- Do not add one back on your own judgement, and do not leave a commented-out stub inviting someone else to.

### 0.2 The first-order price is $33, stated as a price

Changed from $29 on 3 Sep. **State the number. Never present it as a discount** — no "25% off," no percentage anywhere, no crossed-out $44.99 in body copy, no "first-time customer" badge, no deadline. Reasoning in `offer/2026-09-03-first-order-price-framing.md`.

The one exception is the buy drawer — see §4.1, item 3, which is explained there and is deliberate.

Two copy lines were rewritten rather than recalculated because they were built around $29 being exactly a dollar a day. Copy v4.1 flag 3 has the detail. Take every price string from the copy file; don't compute any of them yourself.

---

## 1. What this page is for

One job: convert a stranger who already owns an electrolyte product into a first-time buyer of a $33 bag.

**Audience:** men, roughly 30–55, who work long physical or high-stress days — trades, first responders, shift workers, active civilians.

## 1.1 Awareness level — the constraint that drives the structure

**This reader is product-aware. They already own an electrolyte stick.** They are not asking *why am I tired at 2pm.* They are asking *why would I switch.*

Ian Stanley, reviewing earlier builds:

> "You're in a product-aware market… The people who are clicking on this already know hydration salts exist. You don't need to explain to them this."

> "The job of the first line is to get them to read the second line. Not to sell the product."

**This forbids:**

- Opening with problem agitation of any kind.
- Opening by listing sodium, potassium and magnesium. Those are what everyone else has.
- Burying palatinose. It is named in the third line of the page and it stays there.

The v3 copy already satisfies all of this. The risk in this build is reintroducing it, not creating it.

---

## 2. Visual system — unchanged from v2

- **Dark text on a light ground.** Not the A1 page's dark tactical treatment. Two thousand words of reversed-out type does not get read.
- **Georgia (or equivalent screen serif), 17px minimum on mobile**, 19px desktop, line height 1.6, measure 40–80 characters.
- Single column throughout. **No element on this page scrolls horizontally.** (v3 permitted it for the comparison table; there is no table — see §0.1.)
- Tokens, type scale and rhythm rules carry forward from v2 unchanged.
- Dark mode out of scope. Set colours explicitly.

---

## 3. Section order and depth targets

**Depth percentages are targets at 375×812 and must be verified after build.** The page is substantially shorter than v2, so these are recalculated from scratch — do not carry v2's numbers across.

| # | ID | Section | Depth | Copy key |
|---|---|---|---|---|
| 1 | `hero` | Headline + palatinose reveal | 0% | `S1_HERO` |
| 2 | `trust` | Trust ribbon | ~7% | `S2_TRUST` |
| 3 | `why-carb` | Why a carbohydrate is in a hydration product | 9–20% | `S3_WHY_CARB` |
| 4 | `cta-1` | **Buy button 1 + sticky bar activates** | **20%** | `CTA_PRIMARY` |
| 5 | `formula` | What we decided to do different — and the full panel | 21–40% | `S4_FORMULA` |
| 6 | `compare` | Put the labels next to each other — no table at launch | 40–44% | `S5_COMPARE` |
| 7 | `cta-2` | Buy button 2 | 44% | `CTA_PRIMARY` |
| 8 | `why-others-quit` | Why other packets quit on you | 45–56% | `S6_WHY_OTHERS_QUIT` |
| 9 | `built-for` | Who we built it for — Callon | 56–67% | `S7_BUILT_FOR` |
| 10 | `cta-3` | Buy button 3 | 67% | `CTA_PRIMARY` |
| 11 | `before-after` | What that can look like | 68–73% | `S8_BEFORE_AFTER` |
| 12 | `keep-yours` | We're not asking you to throw anything away | 74–78% | `S9_KEEP_YOURS` |
| 13 | `offer` | Your first bag is $33 | 79–84% | `S10_OFFER` |
| 14 | `cta-4` | **Buy button 4 — inline offer module** | 84% | `S10_OFFER` |
| 15 | `guarantee` | Try it for 90 days | 85–89% | `S11_GUARANTEE` |
| 16 | `cta-5` | Buy button 5 | 89% | `CTA_PRIMARY` |
| 17 | `faq` | Frequently asked questions | 90–96% | `S12_FAQ` |
| 18 | `close` | Close | 96–99% | `S13_CLOSE` |
| 19 | `cta-6` | Buy button 6 — final | 99% | `CTA_PRIMARY` |

**Nothing renders after `cta-6`** except the footer.

### Why `cta-1` sits at 20%

The approved copy contains only three buy buttons, and the first of them falls after the comparison table at roughly 46% depth. **That is too deep.** Only 28% of this audience's mobile sessions reach 25% depth on the existing PDP; a first ask at 46% would be seen by almost nobody.

`cta-1` is therefore a placement addition, not new copy. It sits immediately after `why-carb`, which is the earliest point the reader has both the differentiator and the reason it matters. The sticky bar activates here, so from 20% onward there is always a way to buy on screen.

### Section IDs retired from v2

`mechanism`, `panel`, `why-yours-quits`, `transformation` no longer exist. Their v3 equivalents are `why-carb`, `compare`/`formula`, `why-others-quit`, `before-after`. Analytics event names change with them — see `analytics-events.md` v3.

---

## 4. Interaction spec — carry forward from the v2 build, verified working

**Do not rewrite any of this.** It was measured working in headless Chromium: focus moves into the drawer on open, returns to the triggering button on close, Escape closes, and scroll position is preserved exactly.

### 4.1 The buy drawer

Every in-body buy button (`cta-1`, `2`, `3`, `5`, `6`) opens a drawer that slides up over a scrim. **It must not scroll the page.** Evidence: on a supplement store at 3,000+ conversions per variation, a mobile button that scrolled the reader to the buy area produced +6% add-to-cart clicks and no significant order difference; a drawer produced +11.8% clicks and +5.2% orders at 98% significance.

Drawer contents, in order:

1. Product image thumbnail
2. Flavour selector — B1 Blue Raspberry / B2 Lemon Lime. Required, nothing preselected, primary action disabled until one is chosen
3. Price line: `$33` with `$44.99` struck through, labelled `first bag`
4. Second-bag upgrade as a distinct row: `Add the other flavor — $19` / `Same box. No extra shipping.` **Unchecked by default.** Total updates to `$52` when checked
5. Guarantee line: `90 days to try it. Keep the bag either way.`
6. Primary action: `Try your first bag — $33`, label reflecting live total

⚠️ **Item 3 is the only crossed-out price allowed anywhere in this build, and it is deliberate.** The page argues the value and states $33; the drawer is where someone who has already decided verifies what they'll be charged, and $44.99 is the real catalogue price they'll pay on reorder. Showing it there is disclosure. Showing it in body copy, in the sticky bar, in the hero, or in an ad would be discount framing, which §0.2 forbids. If Tracy would rather the drawer show $33 alone, that's a one-line change — flagged in §8.

Behaviour: scrim click, Escape and an explicit close all dismiss. Focus trapped while open, returned on close. Page scroll locked via `body{position:fixed; top:-Ypx}` with the offset captured **before** the lock and restored on close. 250ms slide, disabled under `prefers-reduced-motion`. Submits to cart and proceeds straight to checkout.

### 4.2 The sticky bar

Hidden until the user scrolls past `cta-1`. Once shown, persists. Hidden while the drawer is open. Compact — product name, `$33`, button. **No struck-through price in the bar.** Respects iOS safe-area insets.

### 4.3 The inline offer module (`cta-4`)

The one place the buy interface renders inline rather than as a drawer. Flavour selector, second-bag row, guarantee line, primary action. Same submit behaviour.

### 4.4 FAQ accordion

Native `<details>`/`<summary>`. First item open, rest closed. Each open emits an event with the `id` given in the copy file.

---

## 5. The comparison section (`S5_COMPARE`) — no table, permanently

**There is no comparison table in this build. This is a decision, not an omission.** Summary for builders is in §0.1; this section is the reasoning.

The competitor figures have never been sourced from current labels. Third-party nutrition aggregators lag reformulations, Liquid I.V. has reformulated and expanded its line, and serving sizes differ across the category. The section opened with *"You don't have to take our word for it. Look at the numbers"* and then showed an empty table — a promise the page could not keep, made to the most label-literate audience in the category.

Rather than block launch on sourcing, the section now keeps its framing and hands the comparison to the reader. Our own panel sits directly above it in `S4_FORMULA`; the section points at that and invites them to go read the back of whatever they already own. That is a stronger move for this audience anyway — a comparison you hand someone is marketing, one they run themselves is proof.

`S4_FORMULA` still makes the comparison in prose — *"Some had a lot of sodium but not much potassium. Some had very little magnesium."* Directionally true, nothing to substantiate.

### The table is not coming back

**Closed out 3 Sep.** Callon reviewed the table-less section in his copy pass and kept it. That converts a launch-scope decision into a permanent one — the section is now the section as designed, not a version waiting on data. Do not reinstate the table without a new decision from Tracy and Callon. Two supplement-facts panel images were added to `S4_FORMULA` in copy v4 and now carry the proof directly; they are what the reader compares against, in place of a table.

If that decision is ever reopened, the constraints below still hold.

Build it as a real table, not an image. Readable at 375px, horizontal scroll in its own `overflow-x: auto` container. Never name a competitor — generic descriptors only, per the 24 Aug decision. Re-insert directly beneath "Look at the numbers." Add a dated footnote: *"Figures from published labels, [month year]. Formulations change — check the panel on whatever you're using."*

**Do not restore the chloride row.** Valor's declared 1,200mg is essentially the chloride that arrives with 800mg of sodium as sodium chloride. LMNT's undeclared chloride, by the same arithmetic on 1,000mg of sodium, is higher. A dash in that column would read as an advantage that doesn't exist, and this audience will do the maths. Full workings in `comparison-table-sourcing.md`.

## 6. Brand voice constraints

Read `core/brand-voice.md` and `memory/glossary.md`. Load-bearing for this page:

- **Callon Nichols** — spelled C-A-L-L-O-N. The v3 copy says "former Marine Corps officer"; that is Callon's own phrasing and is approved. Never "infantry."
- **EMT-certified**, never implied to have worked as an EMT running calls.
- Co-founder: **"spent over a decade in the SEAL teams."** Exact wording, never a named unit.
- Callon is **not a firefighter** and claims no proximity he doesn't have.
- **No exclamation points.** No manufactured urgency — no countdowns, no stock counters.
- **Nothing about cramps**, in any form. Standing rule.
- **No "sugar-free" or "zero sugar."** The panel declares 4g total sugars.

⚠️ **Open compliance item:** whether the DSHEA disclaimer runs sitewide is still undecided. Reserve the footer slot.

---

## 7. Technical requirements

- Meta Pixel + CAPI, with a **custom conversion distinct from the A1 page's Purchase event** — the two campaigns must not optimise against each other.
- Microsoft Clarity from day one.
- Every event in `analytics-events.md` v3 fires.
- `noindex, nofollow`. Excluded from sitemap. **The $33 must never be discoverable from the main site** — the $44.99 anchor has to survive.
- No external font hosts, no CDN scripts, no third-party embeds beyond pixel and Clarity.
- Mobile-first at 375px. Total page weight under 1.5MB. LCP under 2.5s on mid-range mobile over 4G.
- Semantic landmarks, one `h1`, headings in order, visible focus states, 4.5:1 contrast on body text.

---

## 8. Open items before launch

| # | Item | Owner |
|---|---|---|
| 1 | ~~Comparison table — cut from launch by decision~~ **Closed 3 Sep: cut permanently, see §0.1 and §5** | — |
| 2 | 🛑 Shipping time — the FAQ has `[INSERT CONFIRMED SHIPPING TIME]`. Only remaining hard blocker | Callon |
| 3 | Approve the trust ribbon (addition, not in the EGC copy) | Tracy |
| 4 | Approve the guarantee line at the buy buttons (addition, assembled from approved copy) | Tracy |
| 4b | ~~Approve the two new closing lines in `S5_COMPARE`~~ **Closed 3 Sep: Callon kept them** | — |
| 5 | Approve the single standardised button label | Tracy |
| 6 | 🛑 Shopify: checkout charges $44.99, not $33, and the second-flavor upgrade adds $44.99 rather than $19. No discount mechanism configured. **Blocks traffic.** Needs a live test purchase | Tracy |
| 8 | ~~First-order price~~ **Closed 3 Sep: $33, stated as a price, no percentage. See §0.2** | — |
| 9 | Confirm the drawer keeps the struck-through $44.99 (§4.1 item 3) — the only crossed-out price in the build | Tracy |
| 7 | DSHEA disclaimer — sitewide or not | Callon |

## 9. Out of scope

Reviews and testimonials (no volume yet). Video — a priority for the next revision once footage exists. Subscription on this page; the ascension happens post-purchase. A1 cross-sell anywhere on the page.

Several of Ian's angles are ad material rather than page material — the "why is it expensive" ingredient explainer, the founder-podcast format, the not-first-but-better story as a standalone hook. Those belong in a creative brief. His own note: *"Everything I say doesn't mean it has to be the lead… all of those can also be different ads."*
