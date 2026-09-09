# Copy: Valor Vitals Hydration Long-Form Sales Page

**Version:** 4.1 — 2026-09-03
**Source:** v3.0 with Callon's review edits applied, plus the 3 Sep price decision ($29 → $33). Callon made his changes as tracked changes in `Valor_Vitals_Landing_Page edits.docx` (Drive `1ZS_DJM8maPLZHi8P-cd0cliGWAXtZkQ4`) and Tracy accepted all of them on 3 Sep. This file is the accepted text, re-keyed to PRD section IDs.
**Prior versions:** `_superseded/copy-v3-archive.md`, `_superseded/copy-v2-archive.md`, `copy-hydration-sales-page-v1-archive.md`

**Builder: use this verbatim.** Every section is keyed to a PRD section ID. If something you need isn't here, flag it — don't write it.

---

## What changed in v4

Twelve edits, all Callon's, all accepted:

1. **`S1_HERO`** — palatinose is now "a slow-release carbohydrate **for steady energy** derived from beet sugar."
2. **`S4_FORMULA`** — heading replaced: *"We Were Late to the Electrolyte Category. That Helped."* → **"What we decided to do different."** Sentence case and the closing period are his; left as written.
3. **`S4_FORMULA`** — "Four grams of slow-release carbohydrate **for steady energy over a longer period.** 25 calories."
4. **`S4_FORMULA`** — two supplement-facts panel images added as explicit slots. New to the copy doc; see the manifest note below.
5. **`S5_COMPARE`** — Callon accepted the table-less version, including the two lines that were flagged for approval in v3. **The comparison table is now cut for good, not deferred.** The v3 re-insert note is gone and `comparison-table-sourcing.md` is closed out.
6. **`S6_WHY_OTHERS_QUIT`** — the long-days paragraph rewritten in his language: mountains, 40-pound pack, field training, 100-plus-degree heat.
7. **`S6_WHY_OTHERS_QUIT`** — "Enough carbohydrate to support the absorption process, but only 4 grams." → **"Something that could help with energy over a sustained period of time."**
8. **`S7_BUILT_FOR`** — "…room for one built differently **and tailored to meet the needs of people who wanted to be an asset to themselves and those around them in any situation.**" Founder portrait added as an explicit slot.
9. **`S8_BEFORE_AFTER`** — both halves rewritten. "There's no caffeine to account for later." was cut.
10. **`S12_FAQ` `timing`** — "There's no stimulant timing to worry about, just a slow and steady energy release to help keep you pushing."
11. **`S12_FAQ` `added_sugars`** — the mechanism sentence replaced with an outcome sentence, and "There is no added cane sugar." deleted. **This was a do-not-edit block in v3.** See flag 2.
12. **`S12_FAQ` `shipping`** — placeholder resolved: "We typically ship out the next business day after we receive your order."

Also in the accepted doc and applied: `S12_FAQ` `difference` and `S13_CLOSE` both pick up the steady-energy phrasing.

**v4.1 (same day):** first-order price moved from $29 to $33. See flag 3 — three lines were rewritten rather than recalculated.

---

## Three things the builder and Tracy need to see before this ships

### ⚠️ 1. "Made in the USA" — corrected here, not as Callon wrote it

Callon's document says **Made in the USA** in the trust ribbon and again in the footer. Both read **Manufactured in the USA** below.

This is the one place v4 does not follow the accepted document. "Manufactured in the USA" was locked on 2026-08-27 because some ingredients are sourced outside the US, which makes "Made in the USA" an FTC unqualified-origin claim the product can't support. The edit he made was to other copy in those blocks; the origin line was almost certainly carried along rather than chosen. **Confirm with him, but do not ship "Made in the USA."**

### ⚠️ 2. "Steady energy" is now a claim, in eight places

v3 was written to describe what palatinose *is* and let the reader draw the conclusion — "how slowly it breaks down," "carbohydrate participates with sodium in the absorption process." Callon's edits replace several of those with what it *does for you*: steady energy, energy over a sustained period, no spike and crash.

That is better copy. It is also a structure/function claim, and **the sitewide DSHEA disclaimer decision is still open.** The `added_sugars` FAQ is the sharpest case: it was written as a compliance-safe answer and marked do-not-edit, and it now ends on an outcome. Everything below ships as he wrote it, but the disclaimer decision should be closed before this page takes traffic, and if it lands the conservative way these are the eight lines to revisit:

`S1_HERO` · `S4_FORMULA` (palatinose line) · `S6_WHY_OTHERS_QUIT` (two) · `S8_BEFORE_AFTER` After block · `S12_FAQ` `timing` · `S12_FAQ` `added_sugars` · `S12_FAQ` `difference` · `S13_CLOSE`

### ✅ 3. First-order price is now $33 — decided 3 Sep

Callon proposed 25% off a first-time order in place of the flat $29. **Tracy took the number and not the framing: the first bag is $33, stated as a price.** Nothing on this page says "25% off," shows a percentage, or crosses out $44.99 in body copy. The reasoning is in `offer/2026-09-03-first-order-price-framing.md`; the short version is that a percentage puts the reorder price on screen at the moment of purchase and replaces an anchor the page spends 2,000 words building.

$33 is 26.7% off the $44.99 catalogue price. The second flavor stays at **$19**, so two bags is **$52**.

**Two lines could not survive the change and were rewritten, not recalculated:**

| v4.0 | v4.1 | Why |
|---|---|---|
| "about **97 cents a day**" (`S5_COMPARE`) | "about **$1.10 a stick**" | 30 sticks at $33 is $1.10. The figure changes and the sentence still works |
| "**Under a dollar a day.**" (`S10_OFFER`) | "**That's a month of hydration.**" | The whole point of that line was that 97¢ cleared a round number. At $1.10 it doesn't, and restating the threshold only draws attention to crossing it. Replaced with duration, which is the honest value story at $33 |
| "About **97 cents each**." (`S13_CLOSE`) | "About **$1.10 each**." | Same arithmetic |

**Every price string on the page, for the next time this moves:**

| Where | String |
|---|---|
| `CTA_PRIMARY` | `Try your first bag — $33` (all six buy buttons and the sticky bar) |
| `S5_COMPARE` | "$1.10 a stick" · "$19" |
| `S10_OFFER` | heading "Your First Bag Is $33" · "$33" · "$1.10 per stick" · "$19" · "$44.99" |
| `S12_FAQ` `subscribe` | "$33" · "$44.99" |
| `S12_FAQ` `flavor` | "$19" |
| `S13_CLOSE` | "$33" · "$1.10 each" |
| `FOOTER` | "$33" |

⚠️ **Still blocking, unchanged by this decision:** checkout charges $44.99. No discount mechanism is configured in Shopify, and the second-flavor upgrade adds $44.99 rather than $19. Needs a live test purchase before any traffic.

📌 **The Batch 10 ads carry no price**, so this change costs nothing in creative. The first number a click sees is on this page.

---

## `S1_HERO`

# Every Electrolyte Stick Has the Same Three Ingredients. We Added a Fourth.

It's called palatinose.

You've probably never seen it on an electrolyte label because almost nobody in this category uses it.

Most hydration packs have sodium, potassium, and magnesium. So does ours. We use them in what we believe to be the right ratios.

But we added something else.

Palatinose is a slow-release carbohydrate for steady energy derived from beet sugar. The technical name is isomaltulose.

And before the word "carbohydrate" loses you: it's only 4 grams of carbohydrate and 25 calories per stick.

That's it.

Palatinose has a stronger molecular bond than table sugar, so your body breaks it down four to five times more slowly. It's low glycemic, with a glycemic index of 32.

And that matters for more than energy.

---

## `S2_TRUST`

Veteran-owned · Manufactured in the USA · 90-day guarantee · No stimulants

*(Origin wording corrected from the accepted document — see flag 1 above.)*

---

## `S3_WHY_CARB`

### Here's Why We Put a Carbohydrate in a Hydration Product

Your small intestine absorbs glucose and sodium together.

That's one of the basic principles behind oral rehydration. When carbohydrate is available alongside sodium, it participates in the transport process your body uses to absorb sodium and fluid.

The difference with palatinose is how slowly it becomes available.

Regular sugar is broken down quickly. Palatinose breaks down more slowly and is absorbed along the full length of the small intestine.

So instead of having the carbohydrate available for a short period, it remains available for that sodium-glucose transport process over a longer window.

If you've ever heard of someone taking casein protein before bed because it releases amino acids more slowly than other proteins, it's a similar idea.

Slow release is the point.

We wanted a hydration product for long days, so using a carbohydrate that gets burned through quickly didn't make much sense to us.

And using no carbohydrate at all meant leaving out part of the absorption equation.

So we added palatinose.

---

## `CTA_PRIMARY`

*(One label, used at every buy button on the page and in the sticky bar.)*

**Button label:** `Try your first bag — $33`

**Supporting line beneath, small:** 30 sticks. 90 days to try it. Keep the bag either way.

---

## `S4_FORMULA`

### What we decided to do different.

There were already a lot of electrolyte products on the shelf when we started working on ours.

That meant we didn't have to guess.

We could turn over the bags, read the labels, and see exactly what everybody was doing.

Some had a lot of sodium but not much potassium.

Some had very little magnesium.

Some had plenty of fast sugar.

Some removed the carbohydrate entirely.

We took what we learned and built the formula we wanted to use ourselves.

Here's what's in one stick of Valor Vitals Hydration:

**800mg sodium**

**300mg potassium**

**75mg magnesium, from magnesium malate**

A lot of inexpensive formulas use magnesium oxide. We chose magnesium malate.

Then there's another number on our label most people probably aren't used to looking for:

**1,200mg chloride.**

Most people hear "chloride" and think about a swimming pool.

But chloride is also an electrolyte. In fact, it's one of the major electrolytes in your body.

And each stick also contains:

**100mg vitamin C — 111% of the Daily Value.**

Then there's the ingredient that started this whole conversation:

**4g palatinose.**

Four grams of slow-release carbohydrate for steady energy over a longer period. 25 calories.

No caffeine. No stimulants. No artificial dyes. No added cane sugar.

`[IMAGE: B1 Blue Raspberry — supplement facts panel]`

`[IMAGE: B2 Lemon Lime — supplement facts panel]`

And we actually wanted it to taste good.

That sounds obvious until you've tried enough electrolyte products. A formula doesn't do you much good sitting in your cabinet because you hate drinking it.

Valor comes in **B1 Blue Raspberry** and **B2 Lemon Lime**.

📌 **Builder note.** The two panel images are new in v4 and land where the comparison table used to. Both assets exist — the `-Back.png` renders listed in `assets-manifest.md`. They now carry the proof on their own: the section says "read the label," so the label has to be legible. Ship them large enough to read on a 375px screen, tappable to zoom, and check that the printed panel matches the figures above it before launch.

---

## `S5_COMPARE`

### Put the Labels Next to Each Other

You don't have to take our word for it.

Look at the numbers.

Then go turn over whatever's in your cabinet and read the back of that one.

That's the argument.

📌 **The comparison table is cut, permanently.** It was pulled from launch because competitor figures were never sourced from current labels. Callon reviewed the table-less section and kept it, so this is now the section as designed rather than a version waiting on data. Do not reinstate the table without a new decision. `comparison-table-sourcing.md` is retained as a record of what was found and why the chloride row should not come back.

30 sticks. Your choice of B1 Blue Raspberry or B2 Lemon Lime.

That works out to about **$1.10 a stick.**

And if you want to try both flavors, add the second bag for **$19**.

It ships in the same box. No extra shipping.

---

## `S6_WHY_OTHERS_QUIT`

### So Why Do Other Hydration Packets Quit on You?

Most electrolyte products were built around a workout.

You mix one before you train, while you train, or afterward. You get your electrolytes. Then you move on.

That's fine if that's what you need.

But some days don't end after an hour.

You might be in the mountains with a 40-pound pack, pushing up the mountain, or out in the field for days training. You might have a long shift that demands something from you the entire time, in 100-plus degree heat.

That's the use case we had in mind.

A zero-sugar electrolyte product gives you electrolytes without carbohydrates.

A traditional sports drink gives you electrolytes with a much larger amount of faster sugar.

We wanted something between those two.

Something that could help with energy over a sustained period of time.

That's why palatinose is there.

📌 **Punctuation repaired, wording untouched.** The accepted document has a missing period and a doubled period in the long-days sentence — a merge artifact, not a choice. Commas added after "pushing up the mountain" and "the entire time" so the sentence parses on first read. "100+" spelled as "100-plus" because a plus sign reads as a typo in body copy at 17px.

---

## `S7_BUILT_FOR`

### This Is Who We Built It For

`[IMAGE: Callon Nichols, Valor Vitals co-founder, in the field during his Marine Corps service]`

My name is Callon Nichols.

I'm a former Marine Corps officer and certified EMT.

I earned a perfect score on the Marine Corps Physical Fitness Test. I climbed Kilimanjaro. And I ran the Marine Corps Marathon in my combat boots and utilities.

I've asked a lot from my body.

Eventually, I started paying more attention to what I was putting back into it.

I started Valor Vitals with a friend who spent over a decade in the SEAL teams.

One idea from the Marine Corps stuck with me: take care of your gear.

Your body is part of that.

So when we started making products, we made things we actually wanted to use.

That's where this hydration formula came from.

Not because the world needed another electrolyte packet.

There are already plenty of those.

We thought there was room for one built differently and tailored to meet the needs of people who wanted to be an asset to themselves and those around them in any situation.

Something for the person whose day lasts longer than their workout.

📌 **Builder note.** The portrait slot is new in v4. Real photography only — `media/Callon USMC images/`, Tracy picks the frame. Do not generate one, do not substitute stock, and do not ship a generic silhouette. If the pick isn't made, leave a visibly marked placeholder.

⚠️ **Credential lock, unchanged.** "Former Marine Corps officer," never infantry. "Certified EMT" — he holds the certification and never worked as an EMT running calls. Andrew is "a friend who spent over a decade in the SEAL teams," that phrasing exactly, never a named unit. Full rule in `memory/glossary.md`.

---

## `S8_BEFORE_AFTER`

### What That Can Look Like

**Before:**

You already have electrolyte packets in the cabinet.

You go out, push yourself hard in the mountains, on a long day of training, or face a day on the job that takes everything out of you.

You know you have more to put out, but need something to help you get there.

**After:**

You understand what was missing from the product you were using.

You've got electrolytes in the amounts we chose for our own formula, plus a slow-release carbohydrate to give you a steady energy release and not just a rush of sugar leading to a crash.

No complicated routine.

One stick in water.

Then you get on with your day.

📌 **Stray paragraph removed.** The accepted document has an orphan "." between the Before block and the After heading — a merge artifact. Nothing else in this section was touched.

📌 **Photography gap — flag, don't fill.** Real trades and outdoor-work photography for this section still doesn't exist. Ships text-only. Authenticity Rule applies.

---

## `S9_KEEP_YOURS`

### We're Not Asking You to Throw Away What You Already Bought

Seriously.

Keep the electrolyte packets that are already in your cabinet.

We're not asking you to decide today that Valor is the only hydration product you'll ever use again.

That's a big ask for a bag of powder.

Try one stick on your next long day.

Pay attention to the back half of that day.

Then decide.

That's the ask.

---

## `S10_OFFER`

### Your First Bag Is $33

A bag contains 30 sticks.

Your first bag is **$33**, which works out to about **$1.10 per stick.**

That's a month of hydration.

Choose:

**B1 Blue Raspberry**

or

**B2 Lemon Lime**

Want both?

Add the second flavor for **$19** and we'll put it in the same box with no additional shipping charge.

Future reorders are $44.99 per bag.

There's no complicated protocol and no need to stack it with something else.

Mix one stick with water and drink it.

📌 **Priced at $33 per the 3 Sep decision — see flag 3 at the top of this file.** State the price. Do not add a percentage, a crossed-out $44.99, or a deadline to this section.

---

## `S11_GUARANTEE`

### Try It for 90 Days. Keep the Bag Either Way.

You have 90 days to decide if Valor Vitals Hydration is right for you.

If it isn't, ask for a refund.

We'll refund your purchase.

You don't have to send the bag back.

You don't have to prove how many sticks you used.

There's nothing to mail to us.

You tried it. You didn't like it. We give you your money back.

That's the guarantee.

---

## `S12_FAQ`

### Frequently Asked Questions

**What does it taste like?** *(id: `taste`)*
Valor Vitals Hydration comes in two flavors: **B1 Blue Raspberry** and **B2 Lemon Lime**.

Taste mattered to us because electrolyte products can get very salty very quickly. We wanted something you'd actually want to drink regularly, not something you have to force down because the ingredient panel looks good.

**When should I take it?** *(id: `timing`)*
Mix one stick with water and drink it during the part of your day when hydration matters most to you.

There's no stimulant timing to worry about, just a slow and steady energy release to help keep you pushing.

**Does it have caffeine?** *(id: `caffeine`)*
No.

There's no caffeine or other stimulant in Valor Vitals Hydration.

**Why does the label say "Includes 4g Added Sugars"?** *(id: `added_sugars`)*
That's the palatinose.

Palatinose is a carbohydrate derived from beet sugar, so it has to be declared appropriately on the nutrition label.

Each stick contains **4 grams of carbohydrate and 25 calories**.

We use it intentionally because it breaks down four to five times slower than sucrose, giving you a steady energy release over a longer period without a spike and a crash.

**What if I'm fasting or counting carbohydrates?** *(id: `fasting`)*
Each stick contains **25 calories and 4 grams of carbohydrate**.

If you follow a particular fasting or carbohydrate protocol, use those numbers to decide whether it fits.

**How is this different from the electrolyte product I already use?** *(id: `difference`)*
Start with the label.

Valor contains 800mg sodium, 300mg potassium, 75mg magnesium from magnesium malate, 1,200mg chloride, 100mg vitamin C, and 4g palatinose.

The palatinose is the biggest difference.

Most products in the category either contain no carbohydrate or use a faster sugar.

We chose a small amount of slow-release carbohydrate instead for a steady energy release over a longer period.

**Do I have to subscribe?** *(id: `subscribe`)*
No.

Your first bag is $33. Future reorders are $44.99 per bag.

You can buy the product without committing to a subscription.

**What if I don't like it?** *(id: `guarantee`)*
Tell us.

You have a 90-day money-back guarantee, and you don't have to send the bag back or provide proof of use.

**Which flavor should I get?** *(id: `flavor`)*
If Blue Raspberry sounds like your thing, start with B1.

If you prefer citrus, start with B2 Lemon Lime.

Or add the second flavor for $19 and try both. It ships in the same box with no additional shipping charge.

**How fast does it ship?** *(id: `shipping`)*
We typically ship out the next business day after we receive your order.

⚠️ **Builder note, revised in v4.** `fasting` remains do-not-edit: it states figures and promises nothing, and that is deliberate. `added_sugars` was also do-not-edit in v3 and Callon changed it — the closing sentence now describes an outcome rather than a mechanism. It ships as he wrote it, but it is the first line to revisit if the DSHEA decision lands conservatively. See flag 2.

---

## `S13_CLOSE`

### You Don't Need Another Electrolyte Packet That Looks Like Everything Else

You probably already have one of those.

We made one change that most companies in this category don't make.

We added palatinose, which is derived from sugar beets and releases energy more slowly and steadily than sucrose, without a spike or crash.

Then we built the rest of the formula around what we believe to be the right ratios: 800mg sodium, 300mg potassium, 75mg magnesium malate, 1,200mg chloride, and 100mg vitamin C.

No caffeine. No stimulants. No artificial dyes. No added cane sugar.

Your first bag is $33.

Thirty sticks.

About $1.10 each.

And you have 90 days to try it.

Keep whatever electrolyte product is already in your cabinet.

Take one Valor stick on your next long day.

See what you think.

---

## `FOOTER`

**B1 Blue Raspberry / B2 Lemon Lime**

30 sticks per bag. Manufactured in the USA. Veteran-owned.

90-day money-back guarantee. Nothing to send back.

*[DSHEA disclaimer slot — pending the sitewide decision. Reserve the space.]*
