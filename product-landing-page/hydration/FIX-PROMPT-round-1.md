# Feedback for Claude Code — round 1

**Corrected 2026-08-26 after reading the source.** An earlier version of this file listed six fixes. **Three of them were wrong** — they came from behavioural testing with a flawed test script, before the source was read. Corrections are recorded at the bottom so nobody re-opens them.

The build is in better shape than that first pass suggested.

---

## What passed, verified

Real `<dialog>` drawer · focus moves in on open, returns to the triggering button on close · Escape closes · **scroll position correctly preserved** (visual position identical during lock, scrollY restored exactly on close) · flavour radios unchecked by default with Add-to-cart disabled until one is picked · upgrade unchecked by default, total updates $29 → $48 · sticky bar hidden at load, appears at the first CTA · all instrumented events firing to gtag/fbq/clarity · 9 FAQ accordions · 17px body · no horizontal overflow · zero console errors · zero failed requests · all images real photography with real alt text · DSHEA slot reserved and empty as specified · `noindex, nofollow` set · `fetchpriority="high"` plus a preload on the LCP image · copy matches the copy file exactly, including every credential boundary · no forbidden strings, no manufactured urgency · placeholder for the missing transformation photo rather than an AI fill.

The build's own header flag block is thorough and correct. **Its flags #2 and #5 are the two most important items on this page** and both are addressed below.

---

## ⚠️ THE LAUNCH BLOCKER — not a code fix

The build flagged this itself and it is right: **checkout currently charges $44.99, not $29.**

It sourced the real Shopify variant IDs from `../index.html` (B1 `44474517717091`, B2 `44474517749859`) — good initiative — but both are catalogue-priced at $44.99, and no document supplied a discount mechanism. As built, a customer who completes checkout pays full price, and the upgrade adds another $44.99 rather than $19.

**This is a Shopify configuration task, not a page task.** Before launch, one of:
- an automatic discount that fires on those variants for first-time customers, or
- dedicated $29 / $19 variants (or a bundle SKU) with their own IDs to swap into the page, or
- a discount code applied via the checkout URL

Whichever you pick, the page needs the resulting IDs or code. **Do not run traffic until a live test purchase confirms $29 at checkout.**

---

## ⚠️ LABEL vs COPY — verified against the real panel

I read the B1 back-panel image directly. Valor's headline figures all check out: **sodium 800mg, potassium 300mg (as potassium citrate), magnesium 75mg (as magnesium malate), isomaltulose as Palatinose™ 4g.** Copy is accurate on all four.

Three things the label shows that the copy doesn't handle:

**1. "Includes 4g Added Sugars — 8% DV" is printed on the panel.** The copy says "no added cane sugar" four times. That's technically accurate — palatinose is beet-derived and the FDA classes isomaltulose as an added sugar — but this page spends a whole section training the reader to *go read the panel*. A skeptic who does that, having been told there's no added sugar, finds a line that says there is.

Handle it head-on rather than hoping nobody notices. It fits the brand voice better anyway — this is the "we list every dose openly" brand. Suggested FAQ addition, to sit right after the blood-sugar question:

> **Your label says "Includes 4g Added Sugars." What's that?**
> That's the palatinose, and we'd rather you hear it from us than find it yourself. The FDA counts isomaltulose as an added sugar because of how it's classified, not because of how it behaves — it's derived from beet sugar but bonded differently, which is why it breaks down four to five times slower and lands at a glycemic index of 32 instead of 65. There is no cane sugar, no corn syrup and no artificial sweetener in the bag. The 4g on the panel is the ingredient that makes the product work.

**2. Vitamin C 100mg (111% DV) and Chloride 1200mg (52% DV) appear on the label and nowhere in the copy.** Both are free ammunition for the comparison table — chloride especially, since it's a genuine electrolyte most competitors under-dose or omit. Worth adding rows.

**3. Magnesium is magnesium malate, potassium is potassium citrate.** The 24 Aug brief asked whether we could name a better magnesium form. Malate is a real differentiator against the oxide most cheap products use. That's a specific, checkable claim of exactly the kind this brand's voice is built on.

Also on the label and worth knowing: sweetened with **stevia leaf extract**, and it carries a "not intended for use by persons under 18" caution.

---

## Paste this into Claude Code

```
Five changes to product-landing-page/hydration/index.html. The build is good —
these are refinements, not repairs. Do not change anything not listed here.

CHANGE 1 — Hero image: one bag, not two.

The hero currently shows the B1 and B2 bags side by side. Show one bag only
(B1). Two products at the top presents a choice before the reader has a reason
to choose; the flavor decision belongs in the drawer where it's a real
decision. One bag reads as "this is the thing" rather than "here's our range."

Keep the fetchpriority and preload on the one that remains. Drop the preload
for the removed image.

CHANGE 2 — Add the added-sugars FAQ.

Insert a new FAQ item immediately after "There's a carbohydrate in it — will
that spike my blood sugar?". The exact copy is in FIX-PROMPT-round-1.md under
"LABEL vs COPY", item 1. Use it verbatim. Give it question_id "added_sugars"
in the faq_open event.

This is not optional polish — the printed label says "Includes 4g Added Sugars"
and the page tells readers to go read the label.

CHANGE 3 — Add two rows to the comparison table.

The real panel declares Vitamin C 100mg (111% DV) and Chloride 1200mg (52% DV).
Both are missing from the table. Add them as rows, with the competitor columns
marked as unverified placeholders like the existing ones.

CHANGE 4 — drawer_open fires with the wrong depth.

drawer_open currently reports depth_pct: 0 every time, because it reads
window.scrollY after lockScroll() has already set body{position:fixed}, which
collapses scrollY to 0. Capture the depth percentage BEFORE calling
lockScroll() and pass it through. The scroll lock itself is correct — don't
change it.

CHANGE 5 — Depth targets.

Measured at 375x812, document height 16223px:
  cta-1   27.3%  (target 24%, window 20–28%)
  cta-2   37.3%  (target 36%)  — fine
  cta-3   59.4%  (target 56%)
  cta-4   76.6%, button at 83.6%  (target 68%)  — worst drift
  cta-5   88.3%  (target 80%)
  cta-6   98.1%  (target 97%)  — fine

Tighten vertical rhythm to pull these toward target. #problem is 2366px and
#offer is 2633px — that's where the room is. cta-4's inline offer module is
1217px tall, which is why its button lands 15 points low.

Reduce section padding, paragraph spacing and image block heights. Do not cut
copy and do not reduce the 17px body size or line-height — the readability of
this format is the reason it works.

Also: one instance of "flavour" (British) in the drawer. US brand — "flavor".

After the changes, re-measure and report the depth percentage of all six buy
buttons.
```

---

## Confirmed, no change needed

**Typeface stays Georgia.** The research finds no consistent difference in reading speed or comprehension between serif and sans when text is properly laid out; layout, contrast and size matter more. Georgia is specifically a screen-designed serif with a large x-height. A sans variant measured 294px longer — negligible. If you want to test type, test size (17→18px), not the serif/sans axis.

**Price in the hero, button after the mechanism, stays.** Ian's rule on the 20 Aug call was to move the price *down* the page — with an explicit carve-out for categories where the buyer already has a price anchor. Hydration is that carve-out. The mechanism is the part they don't have an anchor for, so the button waits for it.

---

## Corrections to the earlier version of this file

| Earlier claim | Reality |
|---|---|
| "BLOCKER — the drawer destroys scroll position" | **Wrong.** `lockScroll()`/`unlockScroll()` are implemented correctly. The test script clicked the cta-1 button regardless of scroll position, so focus return moved the page — working as designed. `window.scrollY` reading 0 during lock is expected for the `position:fixed` technique; visual position is held by `top: -Ypx`. Re-tested from cta-5: visual position identical during lock, scrollY restored exactly. |
| "Missing DSHEA slot" | **Wrong.** Present at the footer, reserved and intentionally empty, exactly as the copy file specified. |
| "Hero images have no fetchpriority" | **Wrong.** `fetchpriority="high"` is set on the LCP image and there's a `<link rel="preload">` for it. Images also carry width/height attributes, so no layout shift. |
