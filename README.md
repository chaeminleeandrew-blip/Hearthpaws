# HearthPaws — premium pet storefront

A single-file, dependency-free English storefront for a **US-market premium pet dropshipping store**.
Open `index.html` in any browser — no build step, no CDN, no third-party script.

- Brand: **HearthPaws** — "Premium comfort for the pets who wait for you."
- Palette: cream / moss green / clay. Type: system serif display + system sans body.
- Product photography: **real supplier photos** from the live CJdropshipping listings, downloaded to
  `assets/` (760 × 760 JPEG, ~40–100 KB each) so the cards show the item that actually ships.
  Decorative art (hero, cart thumb for filters) remains hand-written inline SVG.
- Cart: slide-out drawer with quantity controls, subtotal, free-shipping meter ($50 threshold),
  localStorage persistence (`hearthpaws-cart-v2`), keyboard/Escape close, focus return.

> **Live checkout:** the drawer's "Checkout with PayPal" button posts a PayPal Cart Upload form
> (`cmd=_cart`, `business=chaeminleeandrew@gmail.com`, USD, $4.95 flat handling under $50) to
> `paypal.com/cgi-bin/webscr`, with `?checkout=success` / `?checkout=cancel` return states.
> Each cart line's `item_number` is now the **CJdropshipping SKU**, so a paid order can be pasted or
> mapped straight into a CJ order without a lookup table.
> No customer reviews are shown — the reviews section says "Verified reviews — coming soon".

---

## 1. Product lineup — one supplier, four SKUs

**Every purchasable item is a CJdropshipping product.** Orders can be fulfilled end-to-end from a
single CJ account (`CJ6093490`, `chaeminleeandrew@gmail.com`) with no second supplier.

Landed cost = CJ item price **+ CJ shipping to a US address**, read from the live product page
("Total: $…", ship-to US, cheapest available method) on 2026-11-22.

| # | Product (store name) | CJ SKU | CJ item | CJ ship to US | Landed | Retail | Gross margin | After card fees* |
|---|---|---|---|---|---|---|---|---|
| 1 | **The Haven Bed** — Medium 20 in (50 cm) | `CJJJCWMY01390-Grey50cm` | $5.61 | $19.00 | **$24.61** | $89 | 72% | $61.51 (69%) |
| 1 | **The Haven Bed** — Large 26 in (65 cm) | `CJJJCWMY01390-Grey 65cm` | $6.08 | $25.58 | **$31.66** | $109 | 71% | $73.88 (68%) |
| 2 | **SteamGroom 3-in-1** — Ceramic white | `CJYD207827101AZ` | $3.86 | $10.07 | **$13.93** | $39 | 64% | $23.64 (61%) |
| 2 | **SteamGroom 3-in-1** — Blush pink | `CJYD207827102BY` | $3.86 | ≈$8.90 † | **≈$12.70** | $39 | 67% | ≈$24.87 (64%) |
| 3 | **Stillwater Fountain** — Circulation 2 L | `CJMY174605320TG` | $13.16 | $18.70 | **$31.86** | $79 | 60% | $44.55 (56%) |
| 3 | **Stillwater Fountain** — Motion-sense 2 L | `CJMY174605325YB` | $16.92 | $19.64 | **$36.56** | $89 | 59% | $49.56 (56%) |
| + | **Fountain Filter Refill** (cotton set) | `CJMY174605312LO` | $2.94 | $6.47 | **$9.41** | $16 | 41% | $5.83 (36%) |

\* Card fee assumed at Stripe/PayPal 2.9% + $0.30. **Ad spend is not included** — budget 15–25% of
revenue for cold traffic. Blended AOV target **$85–$110** (bed alone $89; fountain + refill $95;
a $39 comb plus filters crosses the $50 free-shipping line).

† Verified price/weight pairs. The Blush pink SKU is lighter (234 g vs 317 g) and its freight was
**estimated** from the verified Ceramic white rate (317 g → $10.07); item price is verified. Treat
pink as ≈$12.70 landed until a sample order confirms it.

### Sourcing notes — read before changing anything

- **CJ's US warehouse does not stock this category at these price points.** Filtering
  `Ship from: United States` for *dog bed*, *pet bed*, *pet water fountain* and *orthopedic pet bed*
  returned either unrelated US stock (collars, cat trees) or Amazon-style items at $44–$170 that leave
  no margin ($96 "luxury small dog bed", $170 pet sofa). The US-warehouse pet catalog is thin.
- So every SKU above ships **from China via CJ**: processing 1–4 days, delivery 4–9 days for the
  electronics and 5–11 days for the bed, tracked (`CJPacket Sensitive` / `LuWei Ordinary US`).
  That is still one supplier, one dashboard, one card — which is what the store needed — but the site
  no longer claims US-warehouse dispatch or 3–7 day delivery.
- **`CJGY1919307` (the old SteamGroom SKU) is dead** — a SKU search returns no product. It was replaced
  with `CJYD207827101AZ`, the same style of misting/UVC comb (30 ml tank, 3.7 V 300 mAh, three mist
  speeds, UVC on long press).
- **Wipes were removed.** There was no CJ equivalent that cleared $14 retail after freight, so the
  add-on strip now carries only the fountain filter refill.
- Inventory is factory-held (`CJ: 0, Factory: 12 000+`) on every SKU. Nothing is pre-bought, so there
  is no stock risk — but also no head start: a big spike in orders depends on the factory's stock.
- Prices move. Re-check each product page before an ad push; the `landed` values in `CATALOG` are
  documentation, not used by checkout maths.

### What each product actually is (copy must match these)

**1. The Haven Bed — plush cave bed, "crystal velvet", gentleman grey**
- Deep rounded cave, long-pile faux fur outside, plush lining, PP cotton fill; the rim is high enough
  for a cat or small dog to tuck its chin over.
- Sizes 20 in (50 cm) and 26 in (65 cm) across. It is a **cat / small-to-medium dog** bed — not the
  orthopedic memory-foam bed for large breeds the first draft of this page described.
- Do **not** claim machine-washable covers, non-slip bases, foam density or "orthopedic support" —
  none are in the supplier description, which lists only "1 × pet bed".
- Watch-outs: it ships compressed and needs a day to loft; returns are dominated by size, so the size
  guidance in the FAQ matters more than the pictures.

**2. SteamGroom 3-in-1 — mist brush with UVC**
- 30 ml water tank sprays a fine mist ahead of the needles (three speeds), UVC light on a long press,
  head clicks out for cleaning, DC 5 V/1 A charging (~150 min), 3.7 V 300 mAh battery.
- Packing list is **the comb only** — no cable, no charger, no oil. Say "USB charging" only if you
  confirm a cable is included; the listing does not.
- Watch-outs: battery items run 4–8% defect rates; buy a sample and test ten charge cycles before ads.
  Keep "quiet" claims modest.

**3. Stillwater Fountain — 2 L stainless fountain**
- 304 stainless top, clear 2 L tank, ultra-quiet pump, US plug adapter; ships with one filter element
  and two cotton pads. Motion-sense version adds the proximity sensor.
- **Corded, not cordless.** No battery, no 4,000 mAh, no dry-run protection claim — those were in the
  old copy and are gone.
- Repeat purchase: the cotton filter set (`CJMY174605312LO`), sold as the add-on.

---

## 2. Where to source

| Supplier | Use it for | Notes |
|---|---|---|
| **CJdropshipping** (`CJ6093490`) | **Everything on the store** | One account, one saved card (`mastercard 2526`), tracked shipping, 1–4 day processing. Product pages show live inventory and freight to the US. |
| CJ US warehouse | — | Checked and rejected for these categories (see above). Worth re-checking quarterly — US stock would cut 5–7 days off delivery. |

Rule of thumb: keep the range at three hero SKUs plus one refill. Add a product only when it is a CJ
SKU whose landed cost is ≤ 45% of the planned retail price.

---

## 3. Operating the store

1. **Order watch** — a scheduled action polls `chaeminleeandrew@gmail.com` for PayPal order mail every
   15 minutes; a real order triggers a fulfilment hand-off.
2. **Fulfilling an order** — PayPal order → cart lines carry the CJ SKU in `item_number` → create the
   order in CJ (`Orders → Store Orders`, or paste the SKU into the cart) → pay with the saved card →
   the tracking number goes back to the customer's PayPal email.
3. **Payment path** — PayPal Cart Upload to `chaeminleeandrew@gmail.com`. Confirm the account can
   receive business payments (a Personal account cannot) with one small live order.
4. **Reviews** — none shown until real orders ship; publish only verified purchases (FTC).
5. **Legal & tax** — real shipping/returns pages, state sales-tax registration, a business entity, and
   only claims that can be substantiated. Delivery estimates on the page (1–4 days dispatch, 4–9 days
   in transit) must stay in line with what CJ actually does.
6. **Publish** — GitHub Pages serves `gh-pages` from `chaeminleeandrew-blip/Hearthpaws`:
   ```
   git add -A && git commit -m "…"
   git push origin main && git push origin main:gh-pages
   ```
   Push to **both** branches; `gh-pages` is what the live URL serves.
7. **Measure** — add analytics (GA4 or Plausible) and a Meta/TikTok pixel before the first ad. Track
   add-to-cart rate (target 8–12%) and checkout start (target 40%+ of carts).

---

## 4. Editing the page

Everything lives in `index.html`.

- **Prices / variants / names / SKUs:** the `CATALOG` object at the top of the `<script>` block. Card
  price markup is static HTML — update both when a price changes.
- **Free-shipping threshold:** `var FREE_SHIP = 50;`
- **Handling fee under $50:** `var SHIP_FEE = 4.95;`
- **Cart storage key:** `hearthpaws-cart-v2` (bump it whenever the SKU list changes, so stale carts
  holding retired items are dropped).
- **Images:** `assets/haven-bed.jpg`, `assets/steamgroom.jpg`, `assets/fountain-life.jpg`
  (cards) and `assets/fountain-product.jpg` (cart thumb). Replace them with a square photo of the
  exact SKU you ship.
- **Colours / type:** CSS custom properties in `:root`.
- **Illustrations:** the hero SVG and the filters cart thumbnail are still inline SVG.

Tested in Chromium at 390 px, 768 px and 1440 px: no console errors, no horizontal overflow, cart
maths correct across variants, quantities, removal, empty state and reload persistence.

Live: <https://chaeminleeandrew-blip.github.io/Hearthpaws/>
