# Claude Code prompt — v3

**The copy was replaced, not edited.** It was rewritten in Email Game Changers and is roughly half the length of v2. Section IDs changed. The interaction layer — drawer, focus management, scroll lock, sticky bar — carries forward untouched.

Open Claude Code at the **`Valor Vitals` root** so the root `CLAUDE.md` loads.

---

## Paste this

```
Rebuild the body of the Valor Vitals hydration sales page to v3.

The copy has been replaced wholesale — it was rewritten in Email Game Changers,
it's about half the length of the current build, and the section IDs have
changed. Treat the existing index.html as a shell whose interaction layer you
keep and whose content you replace.

FILE TO EDIT
  product-landing-page/hydration/index.html

READ FIRST, IN FULL, IN THIS ORDER
  1. product-landing-page/hydration/PRD-hydration-sales-page.md
       v3.0. Read §1.1, §3 and §5 before writing anything.
  2. product-landing-page/hydration/copy-hydration-sales-page.md
       v3.0. All copy, verbatim, keyed by section ID.
  3. product-landing-page/hydration/analytics-events.md
       v3.0. Section IDs and event names changed.
  4. product-landing-page/hydration/assets-manifest.md
       Image mapping and the gaps that stay unfilled.

FOR ANY STRING NOT IN THE COPY FILE
  core/brand-voice.md
  memory/glossary.md

KEEP, DO NOT REWRITE

  The <dialog> buy drawer, the focus trap and focus return, lockScroll and
  unlockScroll, the sticky bar timing logic, and the analytics dispatcher.
  All of it was measured working. The drawer preserves scroll position
  correctly — don't touch it.

  Georgia body face at 17px, single column, dark text on light ground.

  The Shopify variant IDs and cart logic. The $44.99 checkout price is being
  handled separately at wiring — leave it and don't re-flag it.

REPLACE

  Every content section. The old IDs mechanism, panel, why-yours-quits and
  transformation no longer exist. The new order and depth targets are in
  PRD §3. Wire the IntersectionObserver and event names to match
  analytics-events.md v3.

DEPTH TARGETS at 375x812
   cta-1  20%    cta-2  46%    cta-3  67%
   cta-4  84%    cta-5  89%    cta-6  99%

  cta-1 at 20% is the number that matters. The approved copy's own first
  button falls at roughly 46%, which is too deep for this audience — only 28%
  of their mobile sessions reach 25% depth. cta-1 is a placement addition
  immediately after #why-carb, and the sticky bar activates there.

  Six buy buttons, one label: "Try your first bag — $29". The copy file has
  three different labels in it; PRD §3 and the CTA_PRIMARY block standardise
  on one. Use the one in CTA_PRIMARY everywhere.

NO COMPARISON TABLE — read PRD §5

  There is no comparison table in this build. The section keeps its heading and
  its framing and hands the comparison to the reader instead. This is a
  decision, not an omission — the competitor figures were never sourced from
  current labels. Build the section exactly as the copy file has it and do not
  add a table.

RULES

  Do not write copy. Every word comes from copy-hydration-sales-page.md v3.0.
  If something is missing, flag it rather than filling it.
  Do not generate images. Asset gaps stay as visible placeholders.
  The [INSERT CONFIRMED SHIPPING TIME] placeholder in the FAQ stays as-is.

Work section by section in page order and report the depth each lands at as you
go. When you're done, re-measure and report: the depth of all six buy buttons,
the depth at which sticky_bar_shown fires, total page height, and any event in
analytics-events.md v3 that does not fire.
```

---

## What to watch for

**If it rewrites the drawer**, stop it. Focus handling and scroll preservation were verified working and none of it shows up in a screenshot.

**If it reintroduces problem agitation before the mechanism**, that's the failure PRD §1.1 exists to prevent — and it's the most likely instinct on a long-form page.

**If it adds a comparison table**, remove it. There isn't one in this build, and the competitor figures have never been sourced from current labels.

**If it edits the added-sugars or fasting FAQ answers**, revert. Both state figures rather than promising outcomes, deliberately.

**If depth targets come in long**, the room is in `#formula` and `#faq`. Tighten vertical rhythm, not copy, and never the 17px body size.
