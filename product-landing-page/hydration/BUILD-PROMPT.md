# Claude Code build prompt — hydration long-form sales page

## Before you paste

Open Claude Code with the working directory set to the **`Valor Vitals` root**, not the `hydration` subfolder. The root `CLAUDE.md` loads automatically from there and carries the brand voice, the Authenticity Rule, and the founder-credential boundaries. Starting inside `hydration/` skips all of it.

---

## Prompt 1 — plan

```
Build the Valor Vitals Hydration long-form sales page.

Start by reading these four files in this order, in full, before writing any code:

1. product-landing-page/hydration/CLAUDE-CODE-BRIEF-hydration.md
2. product-landing-page/hydration/PRD-hydration-sales-page.md
3. product-landing-page/hydration/copy-hydration-sales-page.md
4. product-landing-page/hydration/assets-manifest.md
5. product-landing-page/hydration/analytics-events.md

Then read core/brand-voice.md and memory/glossary.md for any string you have to
write yourself — button labels, alt text, aria labels.

Output: a single self-contained index.html in product-landing-page/hydration/,
embedded CSS and JS, no build step, no external dependencies.

Three things are the most likely failure modes on this build, so hold them
deliberately:

1. The first buy button must land between 20% and 28% of total page height at a
   375px viewport. Not the hero, not the bottom. 88% of this audience is mobile
   and only 28% of them reach 25% depth, so a button below that is a button
   almost nobody sees.

2. Buy buttons open a drawer in place. They must never anchor-scroll the reader
   to another part of the page. This was A/B tested — the scroll variant produced
   more clicks and no more orders.

3. The sticky bar is hidden at page load and appears only once the reader passes
   the first buy button. Showing it earlier reads as an ad and burns the ask.

Do not write copy. Every word comes from copy-hydration-sales-page.md, keyed by
section ID. If something is missing, flag it rather than filling it.

Do not generate images. If an asset gap is listed in assets-manifest.md, leave a
visually obvious placeholder and list it in a comment block at the top of the
file. The Authenticity Rule in memory/glossary.md is absolute.

Before you write anything: give me your build plan. Section structure, the CSS
architecture you'll use to hit the depth targets, how you'll implement the
drawer and focus management, and anything in the docs that's ambiguous or
contradictory. I want to see the plan before the code.
```

---

## Prompt 2 — build (after you've approved the plan)

```
Plan approved. Build it.

Work section by section in page order rather than writing the whole file at
once. After each section, tell me what depth it lands at so we can catch drift
early instead of discovering the CTA is at 40% when the page is finished.

Wire the analytics events as you build each section, not at the end.
```

---

## Prompt 3 — verify

```
Now verify against the definition of done in CLAUDE-CODE-BRIEF-hydration.md.

Specifically, measure and report:
- Actual depth percentage of each of the six buy buttons at 375px
- Where sticky_bar_shown fires, as a depth percentage
- Total page weight including images
- Any console errors
- Every image missing alt text
- Every event from analytics-events.md that does not fire

Then give me the list of placeholders and unverified numbers still in the page,
so I know exactly what has to be resolved before this can go live.
```

---

## Useful follow-ups

| Want | Say |
|---|---|
| Depth targets missed | "The first CTA is at X%. Tighten the sections above it to bring it to 24% — cut vertical padding and image heights before cutting copy." |
| Drawer feels wrong | "Show me the drawer implementation. Walk me through the focus management on open, escape, and close." |
| Check it on real devices | "Give me a checklist of what to verify on an actual phone that I can't catch in the browser." |
| Before handing to Shopify | "What has to change in this page when it moves from a static file to the Shopify environment? List the integration points." |

---

## What to watch for

**If it starts writing copy**, stop it. The Email Game Changers copy is tested and the file is the source of truth — improvised replacements are the most likely way quality leaks out of this build.

**If it proposes a dark tactical treatment** to match the A1 page, that's a misread. This page is dark-text-on-light deliberately; the reasoning is in PRD §2 and it's the whole reason the format works.

**If it fills an asset gap with a generated image**, that's the one unrecoverable error on this account. The Authenticity Rule exists because this audience spots wrong gear instantly.
