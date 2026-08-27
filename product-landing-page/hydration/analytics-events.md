# Analytics Event Spec: Hydration Long-Form Sales Page

**Version:** 1.0 — 2026-08-26

## Why this file exists

At roughly 44 sessions a day and under one order a day, **a valid A/B test is not available.** Conversion rate will not reach significance this year. The page therefore has to be judged on leading indicators that accumulate hundreds of events a week where orders accumulate a handful.

That only works if the page emits them from day one. Retrofitting instrumentation after launch is how a pivot ends up unreadable — build these in as you build the sections.

---

## Destinations

Every event fires to:
1. **GA4** via `gtag('event', name, params)`
2. **Meta Pixel** via `fbq('trackCustom', name, params)` — except `Purchase`, which uses the standard event
3. **Microsoft Clarity** via `clarity('event', name)` — name only, Clarity takes no params. This is what makes session recordings filterable by behaviour, which at this volume is more useful than the aggregate numbers

Add a `?debug=1` flag that also `console.log`s every event. The build isn't done until every event below is visible in the console.

---

## 1. Scroll depth — section-anchored, not generic

**Do not use generic 25/50/75/100 scroll tracking.** It tells you nothing actionable. Fire when the *top of a named section* enters the viewport, via `IntersectionObserver`, once per session per section.

| Event | Fires when | Why it matters |
|---|---|---|
| `section_view_problem` | `#problem` enters viewport | Did they start reading |
| `section_view_mechanism` | `#mechanism` enters viewport | Did they reach the argument |
| `section_view_cta_1` | `#cta-1` enters viewport | **The single most important number on the page.** Baseline to beat: 11.3% of mobile sessions currently reach 75% depth on the A1 PDP |
| `section_view_founder` | `#founder` enters viewport | |
| `section_view_panel` | `#panel` enters viewport | Did they reach the comparison — the strongest asset |
| `section_view_transformation` | `#transformation` enters viewport | |
| `section_view_offer` | `#offer` enters viewport | Did they reach the price |
| `section_view_guarantee` | `#guarantee` enters viewport | |
| `section_view_faq` | `#faq` enters viewport | |
| `section_view_close` | `#close` enters viewport | Completed the read |

**Params on every one:** `{ section: '<id>', depth_pct: <rounded % of document height>, device: 'mobile'|'desktop' }`

---

## 2. Buy drawer funnel

This is where the buy-box-versus-anchor-scroll question gets answered.

| Event | Fires when | Params |
|---|---|---|
| `drawer_open` | Drawer opens | `{ source: 'cta-1'…'cta-6' \| 'sticky_bar', depth_pct }` |
| `drawer_flavor_select` | A flavour is chosen | `{ flavor: 'B1' \| 'B2', source }` |
| `drawer_upgrade_toggle` | Second-flavour row is checked or unchecked | `{ checked: true \| false, source }` |
| `drawer_dismiss` | Closed without adding to cart | `{ source, seconds_open, flavor_selected: true \| false }` |
| `drawer_add_to_cart` | Add-to-cart submits | `{ source, flavor, upgrade: true \| false, value: 29 \| 48 }` |

`drawer_dismiss` is the one people forget to build and it's the most diagnostic event here — a high open rate with a high dismiss rate means the drawer is wrong, while a low open rate means the page is wrong. Those need different fixes.

---

## 3. Sticky bar

| Event | Fires when | Params |
|---|---|---|
| `sticky_bar_shown` | First becomes visible | `{ depth_pct }` — should always be at `cta-1`. If it fires earlier, that's a bug |
| `sticky_bar_click` | Tapped | `{ depth_pct }` |

---

## 4. FAQ

| Event | Fires when | Params |
|---|---|---|
| `faq_open` | An accordion item opens | `{ question_id: 'taste' \| 'timing' \| 'caffeine' \| 'blood_sugar' \| 'difference' \| 'subscribe' \| 'guarantee' \| 'flavor' \| 'shipping' }` |

Which questions get opened is real qualitative data at this traffic volume — it's the closest thing to a free objection survey you'll get. If `blood_sugar` or `difference` dominate, that content belongs higher on the page.

---

## 5. Commerce

| Event | Notes |
|---|---|
| `AddToCart` | Standard Meta event, mirrors `drawer_add_to_cart`. Include `value` and `currency: 'USD'` |
| `InitiateCheckout` | On checkout redirect |
| `Purchase` | Standard event. **Server-side via CAPI as well as pixel** — the diagnostics found initiate-checkout signal loss, and browser-only tracking at this volume loses too much to be readable |

### ⚠️ Separate the conversion from the A1 page

Create a **distinct custom conversion** for this page's purchase. If the hydration campaign and the A1 campaign optimise against the same event, Meta will chase whichever conversion is cheaper to acquire — which is the $29 order, every time — and the A1 campaign's learning degrades. This mirrors the separate-campaigns rule in the offer strategy doc and it is the technical half of the same decision.

---

## 6. Engagement

| Event | Fires when | Params |
|---|---|---|
| `time_on_page` | 15s, 30s, 60s, 120s, 240s | `{ seconds, max_depth_pct }` |
| `rage_click` | 3+ clicks within 500ms in the same 40px area | `{ element, depth_pct }` — Clarity catches this too, but having it in GA4 makes it countable |
| `page_exit` | `visibilitychange` to hidden | `{ max_depth_pct, seconds, reached_cta_1: true \| false }` |

---

## The scoreboard

What actually gets read at the week 6–7 checkpoint, in priority order:

1. **`section_view_cta_1` ÷ sessions** — did more people reach a buy button than the 11.3% who currently reach 75% depth on the A1 PDP. If this fails, nothing else matters
2. **`drawer_open` ÷ `section_view_cta_1`** — does the ask work once they see it
3. **`drawer_add_to_cart` ÷ `drawer_open`** — does the drawer work
4. **`drawer_upgrade_toggle` checked ÷ `drawer_add_to_cart`** — second-flavour attach rate, against Ian's 35% bump benchmark
5. **Bags per order** — the number that decides inventory velocity
6. **Net new active subscribers** — the account-level scoreboard, tracked separately in Appstle

Conversion rate is deliberately not on this list. It will not be readable in that window, and treating it as the verdict is how a working page gets killed early.
