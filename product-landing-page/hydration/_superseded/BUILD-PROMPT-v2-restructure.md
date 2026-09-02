# Claude Code prompt — v2 restructure

**This is a resequence, not a rebuild.** The v1 interaction layer was measured working in headless Chromium and must survive: the `<dialog>` buy drawer, focus trap and return, the scroll lock, sticky bar timing, the six-button cadence, and the analytics dispatcher. What changes is the order of content sections, the hero, two FAQ items and two table rows.

**Open Claude Code at the `Valor Vitals` root**, not inside `hydration/` — the root `CLAUDE.md` loads from there and carries the brand voice, Authenticity Rule and credential boundaries.

**Out of scope for this pass:** the Shopify checkout price. The page currently submits catalogue-priced variants at $44.99; that's being handled separately when it's wired up to Shopify. Claude Code should leave the existing variant IDs and cart logic alone and not re-flag it.

---

## Paste this

```
Restructure the Valor Vitals hydration long-form sales page to v2.

This is a RESEQUENCE, not a rebuild. The existing interaction layer was verified
working and must survive intact: the <dialog> buy drawer, focus trap and focus
return, lockScroll/unlockScroll, sticky bar timing, the six-button cadence, and
the analytics dispatcher. Do not rewrite any of it.

FILE TO EDIT
  product-landing-page/hydration/index.html

READ FIRST, IN FULL, IN THIS ORDER
  1. sales page copy/2026-08-28-restructure-ian-feedback.md
       Why this is changing. Read §1 and §4.
  2. product-landing-page/hydration/PRD-hydration-sales-page.md
       v2.0. §1.1 is new and is the most important section in the document.
       §3 has the new section order and depth targets.
  3. product-landing-page/hydration/copy-hydration-sales-page.md
       v2.0. All copy, verbatim, keyed by section ID.
  4. product-landing-page/hydration/analytics-events.md
       v2.0. Two section IDs changed; FAQ event ids added.
  5. product-landing-page/hydration/assets-manifest.md
       Image mapping and the gaps that must stay unfilled.

FOR ANY STRING NOT IN THE COPY FILE (button labels, alt text, aria labels)
  core/brand-voice.md
  memory/glossary.md

OPTIONAL CONTEXT, IF YOU WANT THE REASONING BEHIND A SPECIFIC LINE
  sales page copy/2026-08-31-ian-feedback-disposition.md
  product-landing-page/hydration/copy-hydration-sales-page-v1-archive.md

WHY THIS IS CHANGING — read PRD §1.1 before touching anything

The page was written for a problem-unaware reader. The actual reader is
product-aware: they already own an electrolyte stick. They are not asking "why
am I tired at 2pm," they are asking "why would I switch." The page now answers
that in the first screen and spends the rest of its length proving it.

WHAT CHANGES

1. NEW HERO — copy S1_HERO
   Replaces "The Afternoon Wall Isn't Age. It's a Missing Ingredient" entirely.
   Show ONE product image (B1 front), not two. Two bags present a choice before
   the reader has a reason to choose; the flavor decision belongs in the drawer.
   Keep the price line, the calories/carbs line, and the guarantee line.
   Keep fetchpriority="high" and the preload on the image that remains, and
   drop the preload for the removed one.

2. SECTION ORDER — full table in PRD §3. The two biggest moves:
   - #mechanism (palatinose) moves from 18-24% to 5-14%. It is now the second
     section on the page.
   - #panel (comparison table) moves from 38-48% to 14-21%. It is the proof of
     the hero's claim and sits directly behind it.

3. TWO SECTION IDS RETIRED AND REPLACED
   - #problem  ->  #why-yours-quits   (copy S5_WHY_YOURS_QUITS, ~50% shorter)
   - #founder  ->  #built-for         (copy S6_BUILT_FOR, merges the stakes
                                       framing with the founder story)
   Update the IntersectionObserver targets and event names to match
   analytics-events.md v2: section_view_why_yours_quits and
   section_view_built_for replace section_view_problem and section_view_founder.

4. TWO NEW FAQ ITEMS — copy S11_FAQ
   "Your label says Includes 4g Added Sugars. What's that?"  id: added_sugars
   "I'm fasting / on keto / counting carbs. What are the actual numbers?"
                                                             id: fasting
   Do not edit the wording of either. Both are compliance-sensitive: they state
   figures rather than promising outcomes, and that is deliberate.

5. TWO NEW COMPARISON TABLE ROWS — copy S4_PANEL
   Chloride 1200mg and Vitamin C 100mg. Both are on the real B1 panel and were
   missing from v1. Competitor cells stay as unverified placeholders, like the
   existing ones.

6. CARRY FORWARD THE TWO OUTSTANDING V1 FIXES
   - drawer_open reports depth_pct: 0 every time, because it reads window.scrollY
     after lockScroll() has set body{position:fixed}, which collapses scrollY to
     zero. Capture the depth percentage BEFORE calling lockScroll(). The scroll
     lock itself is correct — do not change it.
   - One instance of "flavour" in the drawer. US brand: "flavor".

DEPTH TARGETS at 375x812
   cta-1  21%      cta-2  41%      cta-3  50%
   cta-4  64%      cta-5  74%      cta-6  97%

The v1 build drifted badly in the back half (cta-4's button landed at 83.6%
against a 68% target). The compression comes mostly from the problem block,
which was 2,366px in v1 and is roughly half that in the v2 copy deck. Tighten
vertical rhythm in #offer as well. Do not cut copy, and do not reduce the 17px
body size or the line-height.

WHAT DOES NOT CHANGE
   Georgia body face at 17px, single column, dark text on light ground.
   The drawer, sticky bar and scroll-lock implementations.
   The $29 / $19 second flavor / empty-bag guarantee offer.
   Every credential boundary in memory/glossary.md.
   Generic competitors — never a brand name.
   The Authenticity Rule. No generated imagery, ever.
   The Shopify variant IDs and cart logic. The $44.99 checkout price is being
   handled separately — leave it alone and don't re-flag it.

RULES
   Do not write copy. Every word comes from copy-hydration-sales-page.md v2.0.
   If something is missing, flag it rather than filling it.
   Do not generate images. Asset gaps stay as visible placeholders.

Work section by section in page order, and report the depth each section lands
at as you go, so drift gets caught early rather than at the end. When you're
done, re-measure and report the depth of all six buy buttons plus the depth at
which sticky_bar_shown fires.
```

---

## What to watch for

**If it rebuilds the drawer from scratch**, stop it. That code was measured working — focus moves in on open, returns to the trigger on close, Escape closes, and scroll position is preserved exactly. Rewriting risks all four, and none of them are visible in a screenshot.

**If it reintroduces problem agitation above the mechanism**, that's the exact failure PRD §1.1 exists to prevent. The problem material belongs at 22–30%, not at the top.

**If it softens the added-sugars or fasting FAQ answers** into reassurance, revert them. An earlier draft of the fasting answer claimed the product wouldn't break a fast — it will, and that audience will notice.

**If it names a competitor**, that's a standing decision from 24 Aug, not an oversight. Ian named Element and Liquid I.V. in conversation; the page still doesn't.

**If it flags the $44.99 checkout**, acknowledge and move on. Already known, handled separately.

---

## Follow-ups

| Want | Say |
|---|---|
| Depth targets missed | "cta-1 is at X%. Bring it to 21% by tightening #mechanism and #panel — reduce vertical padding and image heights before touching copy." |
| Verify the interaction layer survived | "Confirm the drawer still traps focus, returns focus to the trigger, closes on Escape, and preserves scrollY exactly. Show me the open and close handlers." |
| Check it renders right | "Screenshot at 375px at the hero, #panel, cta-1 and the drawer open." |
| Before Shopify wiring | "List every integration point that changes when this moves into the Shopify environment." |
