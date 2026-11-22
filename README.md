# HearthPaws — premium pet storefront (preview build)

A single-file, dependency-free English storefront for a **US-market premium pet dropshipping store**.
Open `index.html` in any browser — there is no build step, no CDN, no external image.

- Brand: **HearthPaws** — "Premium comfort for the pets who wait for you."
- Palette: cream / moss green / clay. Type: system serif display + system sans body.
- Illustrations: hand-written inline SVG (no broken image links, nothing to license).
- Cart: slide-out drawer with quantity controls, subtotal, free-shipping meter ($50 threshold),
  localStorage persistence, keyboard/Escape close, focus return.

> **Placeholder content:** reviews, star ratings and the "218 sample reviews" count are template copy,
> clearly labelled in the UI. The checkout button is a preview only — no payment processor is connected.

---

## 1. Product lineup and real economics

Prices as shipped in `index.html`. Supplier costs are **dropship / small-order US-warehouse prices**,
not factory FOB, so they include the item, inbound freight and the supplier's margin.

| # | Product (SKU name) | Supplier cost (US warehouse) | Retail | Gross margin | Contribution after card fees* |
|---|---|---|---|---|---|
| 1 | **The Haven Bed** — orthopedic memory-foam pet bed, washable cover, S–XL | $26.50–$34 (M) · $34–$42 (L) · $42–$48 (XL) | $89 / $109 / $129 | 62–70% | ≈ $54 (M) · $66 (L) · $78 (XL) |
| 2 | **SteamGroom 3-in-1** — steam + de-shed brush, self-clean, USB-C | $8–$13 landed ($7.31–$9.50 item + shipping) | $39 | ≈ 67–70% | ≈ $26 |
| 3 | **Stillwater Fountain** — cordless 74 oz / 2.2 L stainless fountain, 4,000 mAh, motion sensor | $19–$28 | $79 (with 6 filters: $95) | 65–76% | ≈ $50 |
| + | Fountain filter 6-pack (recurring) | $4–$7 | $16 | ≈ 60% | ≈ $11 |
| + | Paw & coat wipes, 3 × 50 | $5–$7 | $14 | ≈ 50–64% | ≈ $7 |

\* Card fee assumed at Stripe's 2.9% + $0.30. **Ad spend is not included** — budget 15–25% of revenue for
cold traffic; the three hero SKUs still leave $18–$36 per order after that.

Blended AOV target: **$65–$95** (bed alone is $89; fountain + filters is $95; wipes/filters are the add-on that
gets a $39 order over the $50 free-shipping line).

### Why each one earns its place

**1. The Haven Bed (orthopedic / calming bed)**
- Problem: aging and large-breed dogs wake up stiff; owners already spend $200+ on vet visits, so $89 for
  "a bed that helps her joints" is an easy yes. Highest price tolerance in the category.
- Low return risk when sizing is right; the cover is washable, which kills the "it got dirty" refund.
- Upsell: XL sizing (+$20–$40), replacement covers, a matching blanket. Attach rate on size upgrades is the
  cheapest revenue in the store.
- **Watch-outs:** dimensional weight is the margin killer — 30 × 24 × 10 in bills as ~52 lb while weighing 8 lb.
  Demand vacuum-compressed packing; put the re-loft time ("give it 24–48 h to fully expand") on the product page
  or you will get "it arrived flat" returns. State foam density (30D–45D is commercial standard) so the listing
  is not just another generic bed.

**2. SteamGroom 3-in-1 (steam grooming brush)**
- Problem: shedding season, matted undercoat, cats that panic at clippers. A fine mist lifts loose fur and dander
  before the bristles pull, so the animal tolerates it — that is the whole ad in one clip.
- Extremely video-friendly (steam + before/after fur), light and cheap to ship, so a $39 price with $10 off
  is an impulse buy rather than a considered purchase.
- Repeat angle: deshedding is seasonal but recurring; bundles with wipes or a second head lift AOV.
- **Watch-outs:** battery/electrical items carry higher defect and support load (expect 4–8% vs ~3% for
  non-electronic goods). Buy a sample, test ten charge cycles, and confirm the supplier ships a US-compliant
  charger. Keep "quiet" claims modest — noise is the #1 return reason for grooming tools.

**3. Stillwater Fountain (cordless stainless fountain)**
- Problem: cats drink too little; owners worry about dehydration and kidney issues. Moving water fixes the
  behaviour, and "no cord to chew, no pump hum at 2 a.m." is a concrete, believable differentiator.
- Stainless top is dishwasher-safe → hygiene story that plastic fountains can't tell.
- **Best repeat-purchase item in the set:** filters every 4 weeks ($16), which is what turns a one-off
  customer into a subscription-ish relationship.
- **Watch-outs:** pumps fail when run dry (choose a model with dry-run protection), and returns on any
  water-contact product should be written off rather than restocked. Check the box size — 12 units per carton
  is typical and bulky.

---

## 2. Where to source

| Platform | Use it for | Notes |
|---|---|---|
| **CJdropshipping** | SteamGroom (CJ SPU `CJGY1919307`, ~$7.51–$18.35 depending on variant), small electronics, QC add-on ($0.30/item) | US warehouse stock, 3–7 day delivery; custom packaging from ~$1.20/carton |
| **Spocket / Zendrop** | Premium US/EU suppliers for the bed and fountain, 2–5 day delivery | Higher unit cost, better retail packaging and fewer defects — worth it for the $89 bed |
| **Petfairs (US warehouse)** | Orthopedic bed reference price: **$26.51/pc, MOQ 1**, free US shipping, 3–7 day delivery | Good benchmark for negotiating other bed suppliers |
| **Yiwu Pet Factory** | 74 oz wireless motion-sensor fountain, **$19.34/pc dropship**, 1-piece MOQ | Also 3.2 L stainless at $43.26 for a premium tier |
| **AliExpress US warehouse** | Fastest, cheapest test of new colourways | 7–12 day delivery is the fallback, not the default — it costs conversion |

Rule of thumb: test on CJ/AliExpress at low volume, then move the winners to a US-warehouse supplier or a
small bulk buy (50–100 units) once you have 50+ sales/month and know your real size mix.

---

## 3. Launch checklist

1. **Replace placeholder content** — reviews, star counts, "218 sample reviews", the `4.8` hero badge.
   Keep the "sample" labels off once real reviews replace them.
2. **Connect a payment path** — pick one:
   - *Fastest:* Stripe **Payment Links** / PayPal Smart Buttons behind the Checkout button (no backend).
   - *Proper store:* Shopify + a dropshipping app (Spocket, CJ's Shopify app, Zendrop), reusing this page's
     copy and illustrations as the theme.
   - Keep the drawer's "Checkout" button pointing at your hosted checkout URL; the current handler only shows
     a preview notice.
3. **Set fulfilment** — connect the supplier account, confirm US-warehouse stock, and order one sample of each
   SKU to your own address before spending on ads.
4. **Legal & tax** — real shipping/returns policy pages, state sales-tax registration (or Shopify Tax),
   business entity, and only claims you can substantiate ("vet-approved" needs an actual vet; "OEKO-TEX" needs
   the certificate — the current copy is aspirational placeholder, rewrite it to match your suppliers).
5. **Publish** — GitHub Pages is enough for the preview:
   ```
   git init && git add . && git commit -m "HearthPaws storefront"
   gh repo create hearthpaws --public --source=. --push
   gh api -X POST repos/:owner/hearthpaws/pages -f 'source[branch]=main' -f 'source[path]=/'
   ```
   Then point a custom domain at it (`CNAME`). Move to Shopify/Vercel/Netlify when you take real payments.
6. **Measure** — add analytics (GA4 or Plausible) and a Meta/TikTok pixel before the first ad. Track
   add-to-cart rate (target 8–12%) and checkout start (target 40%+ of carts).

---

## 4. Editing the page

Everything lives in `index.html`.

- **Prices / variants / product names:** the `CATALOG` object at the top of the `<script>` block.
  Card price markup is static HTML — update both, or drive the cards from `CATALOG` if you add SKUs.
- **Free-shipping threshold:** `var FREE_SHIP = 50;`
- **Cart storage key:** `hearthpaws-cart-v1` (bump it when the SKU list changes).
- **Colours / type:** CSS custom properties in `:root`.
- **Illustrations:** inline `<svg>` blocks inside each `.card-media`, plus the hero SVG and the small
  `THUMBS` map used for cart line items.

Tested in Chromium at 390 px, 768 px and 1440 px: no console errors, no horizontal overflow, cart maths
correct across variants, quantities, removal, empty state and reload persistence.
