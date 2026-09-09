# Hydration page — buy drawer fix brief

**Date:** 9 September 2026
**File under investigation:** `product-landing-page/hydration/index.html`
**Live page:** https://valorvitals.com/pages/hydration-offer

Read the repo `CLAUDE.md` first. Its rules apply to everything below — in particular *flag rather than fill*, *copy comes from the copy file* (`copy-hydration-sales-page.md`), and no manufactured urgency.

---

## Context

This page is the sole destination for the Meta hydration campaign. Batch 10 ran 4–8 September: $312 spend, 11,287 impressions, 109 link clicks, 102 landing page views, 22 add-to-carts, 3 purchases. Cost per purchase was $104 against roughly a $44 order.

Microsoft Clarity data for the same window (126 sessions on this page) points the failure at the buy drawer, not at Shopify checkout. The `/cart` page saw 6 sessions and zero dead clicks. Of the add-to-cart sessions that did not purchase, none originated from this page via a Batch 10 ad.

Traffic composition matters for every fix below: **87% of sessions are inside the Facebook or Instagram in-app browser** — 44 Facebook/iOS, 33 Facebook/Android, 25 Instagram/iOS, 7 Instagram/Android, against 17 sessions in a real browser. Anything you change has to be verified in an in-app WebView, not just desktop Chrome.

---

## Measured evidence

26 sessions on this page recorded dead clicks. They cluster on two elements:

| Clarity element label | Dead clicks |
|---|---|
| `Valor Vitals ▪▫ Lemon Lim…` | 55 |
| `Valor Vitals ▪▫ Blue Rasp…` | 52 |
| `Try your first bag — $33` | 33 |
| `Valor Vitals Hydration, ▫…` | 19 |

Other measured facts from the same window:

- Scroll depth is bimodal: 82 sessions stop under 25%, 24 sessions reach 76–100%.
- `Do I have to subscribe?` is the most-clicked FAQ item on the page (11 clicks).
- FAQ `<summary>` elements show repeated clicks 1–2 seconds apart in several sessions.
- JavaScript errors present are `_AutofillCallbackHandler` and `Error invoking postMessage: Java object is gone` — both Android WebView artifacts, almost certainly not ours.
- One session recorded a 21.4-second page load with a 3.4s LCP (Facebook in-app browser). Every other recorded load was under 2.4s.

---

## Working diagnosis — verify before changing anything

These are hypotheses drawn from reading `index.html` against the Clarity data. Confirm each one in the code before you act on it. If the evidence does not support a hypothesis, say so and stop rather than changing the file.

### 1. The drawer product photo is being tapped and does nothing

`index.html:1412` rewrites the thumbnail's `alt` to `'Valor Vitals ' + FLAVOR_NAME[flavor] + ' hydration, 30-stick gusset bag'` when a flavor is selected. That means the top three rows in the dead-click table above are all the same element — `img.buy-panel-thumb` in the `buy-panel-template` (`index.html:1240`), labelled differently depending on whether a flavor had been picked yet.

That is 126 dead clicks on a non-interactive image, the largest single failure on the page. The likely reason people tap it: the image swaps when a flavor is chosen, so it reads as the flavor control.

Investigate whether the image should select a flavor, whether the flavor tiles are a large enough tap target on a phone, and whether the image is intercepting taps intended for the tiles beneath it. Note that `.flavor-option input` (`index.html:550`) is absolutely positioned at 100% × 100% over its option — check that this overlay is actually receiving taps in a WebView and is not covered by anything.

### 2. The submit button is disabled and carries the same label as the button that opened the drawer

`index.html:1264` ships `<button type="button" class="btn-primary" data-submit disabled>Try your first bag — $33</button>`. It is enabled only once a radio is checked (`index.html:1411`, `submitBtn.disabled = !s.flavor`).

The six page CTAs (`index.html:881, 948, 1000, 1087, 1197`) and the sticky bar (`index.html:1221`) carry that identical label. The top-of-file note at `index.html:36` records this as a deliberate choice.

So a visitor taps "Try your first bag — $33", the drawer opens, they see a button reading "Try your first bag — $33", tap it, and nothing happens — because no flavor is selected yet. Session recordings show exactly this: opener tap, then a dead click, then exit. Sessions that converted show opener → radio → submit.

Investigate options and recommend one rather than picking silently. Possibilities include: pre-selecting a default flavor so the button is never disabled; giving the disabled state a visible reason ("Pick a flavor first"); making a disabled tap scroll to or highlight the flavor group; or differentiating the two button labels. Each has a trade-off — pre-selecting removes friction but also removes a deliberate choice, and the flavor decision was called out as real first-order friction in the Batch 10 offer work.

### 3. `<dialog>` and `showModal()` in the Facebook and Instagram in-app browsers

The buy panel is a `<dialog id="buy-drawer">` (`index.html:1225`). With 87% of traffic in in-app WebViews, confirm that `showModal()`, the backdrop, focus trapping and the close button all behave there — particularly older Android WebView builds. If support is uncertain, propose a fallback and say what it would cost.

### 4. The FAQ accordions

Several sessions show a `<summary>` clicked twice within a second or two. Some of that is open-then-close, but check whether the `<details>` elements respond promptly on touch and whether anything overlays them.

Separately: `Do I have to subscribe?` being the top FAQ click is a purchase objection sitting inside an accordion, on a page whose drawer sells a one-time bag. Do not rewrite copy to address it — flag it and propose where the answer should surface. Any new wording comes from `copy-hydration-sales-page.md` or waits for it.

### 5. Price inconsistency across the store

The store currently presents four different prices for the same product family:

| Surface | Price shown |
|---|---|
| `/pages/hydration-offer` (this page, and its dedicated intro-offer variants) | $33 |
| `/products/b1-hydration` | $44.99 |
| `/collections/all-products` | $40.49 |
| `/products/b2-hydration-copy` (titled "A1 Enhanced Multi-Vitamin with B2 Hydration") | $89.98 |

The repo `CLAUDE.md` still documents $29 as the hydration first-order acquisition price, which no surface matches.

Audit where each figure comes from. `index.html:1276–1277` points at the dedicated intro-offer variants `44552611397731` (B1 Blue Raspberry) and `44552611430499` (B2 Lemon Lime); `index.html:175–189` records why. Do not change prices — report what is set where, flag the `CLAUDE.md` figure as stale, and flag `b2-hydration-copy` as a probable duplicate or mis-titled product for a human decision.

---

## Instructions

1. Read `CLAUDE.md`, then `index.html` in full, then `copy-hydration-sales-page.md` and `analytics-events.md`.
2. Work through items 1–5 in order. For each, state what the code actually shows before proposing anything.
3. Where a hypothesis is not supported by the code, say so and move on. Do not fix a problem that is not there.
4. Items 1 and 2 are the priority. They account for 159 of the page's dead clicks between them.
5. For each fix, propose the change and the trade-off before writing it. Item 2 in particular needs a decision, not a default.
6. Item 5 is audit-and-report only. No price changes.
7. Instrumentation: `analytics-events.md` defines the tracked events. If `drawer_flavor_select` and `drawer_add_to_cart` (`index.html:1418`, `:1441`) are firing but a disabled-submit tap is invisible, add an event for the failed attempt so this is measurable next time rather than inferable from Clarity dead clicks.
8. Verify every change in a mobile viewport and, where possible, in an actual Facebook in-app browser. Desktop Chrome is not a sufficient test for this page.
9. Do not change copy, prices, offer structure, or imagery. Flag anything that seems to need it.
