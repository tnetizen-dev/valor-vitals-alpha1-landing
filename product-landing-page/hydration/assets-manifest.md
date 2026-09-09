# Asset Manifest: Hydration Long-Form Sales Page

**Version:** 2.0 — 2026-09-03
**Changed in 2.0:** section IDs re-keyed to copy v4 (the manifest was still on the v2 IDs). Two supplement-facts panels and the founder portrait are now explicit `[IMAGE:]` slots in the copy rather than suggestions here. Competitor label figures removed from the blocking list — the comparison table is cut permanently.
All paths relative to the `Valor Vitals/` root.

> **The Authenticity Rule applies to every image on this page.** No AI-generated humans, uniforms, gear, apparatus, or station environments. Ever. If a slot below is marked as a gap, leave a visually obvious placeholder and flag it — do not fill it with a generated image. Full rule in `memory/glossary.md`.

---

## Available and mapped

| Section | Asset | Path | Notes |
|---|---|---|---|
| `S1_HERO` | Product hero — gusset bag | `media/Product and brand images/hydration packs/VALORVITALS-B1Hydration-BlueRaspberry-Gusset-30ct-Front.png` | LCP element. Size properly, `fetchpriority="high"`. Consider pairing with the B2 front so both flavors read at a glance |
| `S1_HERO` | Second flavor | `media/Product and brand images/hydration packs/VALORVITALS-B2Hydration-LemonLime-Gusset-30ct-Front.png` | |
| `S2_TRUST` | Logo | `media/valor_vitals_logo.png` | Trust ribbon icons: source or draw as inline SVG. Do not use emoji |
| `S3_WHY_CARB` | Stick pack detail | `media/Product and brand images/hydration packs/VALORVITALS-B1Hydration-BlueRaspberry-Gusset-30ct-Sticks.png` | Shows what a stick actually is — useful right where the mechanism lands |
| `S3_WHY_CARB` | Single stick | `media/Product and brand images/hydration packs/VALORVITALS-B2Hydration-LemonLime-Stick.png` | Alternative to the above |
| `S7_BUILT_FOR` | Callon portrait | `media/Callon USMC images/` — review and select | **Required slot in copy v4**, at the top of the section. `Promotion.webp` and `Callon USMC_1.jpg` are the strongest candidates. Tracy approves the pick before build. Real photography only — no generated substitute, no stock, no silhouette |
| `S4_FORMULA` | Supplement facts, B1 | `media/Product and brand images/hydration packs/VALORVITALS-B1Hydration-BlueRaspberry-Gusset-30ct-Back.png` | **Required slot in copy v4**, immediately after the palatinose line. There is no comparison table any more — these two panels are the proof. Legible at 375px, tappable to zoom. Verify the printed panel matches the figures in the copy before launch |
| `S4_FORMULA` | Supplement facts, B2 | `media/Product and brand images/hydration packs/VALORVITALS-B2Hydration-LemonLime-Gusset-30ct-Back.png` | |
| `S8_BEFORE_AFTER` | Lifestyle — shift work | `media/Lifestyle Photos/vv_lifestyle_EMS.jpg` or `vv_lifestyle_fire_*.jpg` | **Use only the `.jpg` files.** See the caution below |
| Drawer / `cta-4` | Product thumbnail | Gusset fronts, as above | Small render, both flavors |

---

## ⚠️ Caution on the lifestyle library

`media/Lifestyle Photos/` contains a mix of `.jpg` and `.png` files, and the naming pattern suggests some of the `.png` files may be generated or composited rather than real photography — `firefighter extended.png`, `vv_lifestyle_wilderness_fire_action_1.png` and similar.

**Do not use any image from this folder on this page until Tracy has confirmed its provenance.** The audience for this page includes firefighters and EMS, and the Authenticity Rule exists precisely because they will spot a wrong helmet or an impossible piece of apparatus that we can't. When in doubt, ship the page without a lifestyle photo — a missing image costs less than a fake one.

---

## Gaps — flag, don't fill

| Need | Section | Status |
|---|---|---|
| ~~**Comparison graphic**~~ | — | **Closed 3 Sep.** The comparison table is cut permanently (PRD §5). No asset, no figures needed |
| **Trades / outdoor work photography** | `S8_BEFORE_AFTER` | The library skews heavily to fire and EMS. The audience for this page is broader — trades, shift work, active civilians. Real photography for those segments doesn't exist yet. Either run fire/EMS imagery and accept the narrower read, or ship text-only and source photography for v2 |
| **Product-in-use photography** | Any | No shots exist of a stick being poured, a bottle being mixed, or the product in a work environment. This is the single most useful photography gap for this page — a real photo of the product in a hand at a job site would do more than any of the existing assets |
| **Callon on camera, hydration-specific** | `S7_BUILT_FOR` | All existing footage is A1-era. A short founder video above the fold is a v2 priority — CXL cites two tests where above-fold video drove 46% and 25% more sales |

---

## Data that isn't an image but blocks the build

| Item | Blocks | Owner |
|---|---|---|
| **Photo of the actual B1/B2 nutrition panel** | The two panel images in `S4_FORMULA`, and every number in the value stack | Callon |
| ~~**Competitor label figures**~~ | — | **Closed 3 Sep.** No longer blocking — the table is cut. Workings retained in `comparison-table-sourcing.md` |
| **Does the panel show 4g total sugars?** | Whether "no added cane sugar" is the right phrasing, and print risk | Callon |

---

## Image handling

- Hero image eager, `fetchpriority="high"`. Everything else `loading="lazy"`.
- Serve product renders at 2× the largest rendered size, no more. The source PNGs are large — compress before shipping.
- Every image gets meaningful alt text written in the brand voice. Not "product image" — "Valor Vitals B1 Blue Raspberry hydration, 30-stick bag."
- Total page weight target under 1.5MB including images.
- Do not inline images as data URIs.
