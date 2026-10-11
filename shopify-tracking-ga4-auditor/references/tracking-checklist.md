# Shopify Tracking Audit Checklist

For each item: **Status** (Pass / Issue / Critical), **Evidence** (DebugView, Tag Assistant, config), **Fix**.

## 1. Installation method inventory

Identify every way tracking is loaded — overlaps cause duplicates.

- [ ] GA4 via the **Google & YouTube** Shopify app (Shopify's official integration).
- [ ] GA4 via a **Shopify custom pixel** (Settings > Customer events).
- [ ] GA4 via **GTM** (web container) and/or server container.
- [ ] GA4 hardcoded in theme (legacy; flag it).
- [ ] Legacy **Additional Scripts** on the checkout/thank-you page (deprecated — should migrate to custom pixels / checkout settings).
- [ ] Ad platform tags: Google Ads, Meta Pixel/CAPI, TikTok, etc., and how each loads.

**Rule:** Pick one mechanism per platform. Two GA4 installs (app + custom pixel, or app + GTM) is the classic double-count.

## 2. Event coverage

(Detailed parameters in `ga4-event-taxonomy.md`.)

- [ ] `page_view` fires correctly across storefront and checkout.
- [ ] `view_item_list` on collection/listing pages with `items`.
- [ ] `view_item` on PDP with item details.
- [ ] `add_to_cart` on add (with `items`, `value`, `currency`).
- [ ] `begin_checkout` when checkout starts.
- [ ] `add_payment_info` / `add_shipping_info` if used.
- [ ] `purchase` on order completion (once) with `transaction_id`, `value`, `currency`, `items`; optional `tax` and `shipping` are separate numeric parameters.
- [ ] Events fire at the right moment, not on page load by mistake.

## 3. Purchase accuracy and reconciliation

- [ ] `purchase` fires exactly once per order (no thank-you-page refresh double count).
- [ ] `transaction_id` = the Shopify order ID/number (enables dedup and reconciliation).
- [ ] `value` equals the sum of discounted item `price * quantity`, excluding tax and shipping; reconcile this item-revenue basis with Shopify.
- [ ] `currency` always present and correct (esp. multi-currency / Markets).
- [ ] GA4 purchase count reconciles with Shopify orders (within a small, explainable variance).
- [ ] Refunds handled if needed.

## 4. Duplicate detection

- [ ] No two GA4 installs firing the same events.
- [ ] No duplicate purchase from page refresh, back button, or multiple thank-you renders.
- [ ] GTM tags not firing alongside the Google app for the same events.
- [ ] Ad pixels not double-firing (e.g. Meta Pixel + CAPI without dedup `event_id`).
- [ ] Cross-domain checkout not creating a new session / duplicate events.

## 5. Data layer / items payload

- [ ] `items` array includes at least one of `item_id` or `item_name` (both recommended), plus `price` and `quantity` for value validation, and ideally `item_brand`, `item_category`, `item_variant`.
- [ ] `item_id` is consistent across events and matches the product/variant ID used in Merchant Center/feeds.
- [ ] `currency` is a three-letter ISO 4217 string; `value`, `price`, `quantity`, `tax` and `shipping` are numbers when supplied.

## 6. Checkout & thank-you specifics (Shopify reality)

- [ ] Checkout/thank-you tracking uses Customer Events (Web Pixels API) or checkout settings, not deprecated additional scripts.
- [ ] On Plus / checkout extensibility, pixels run in the sandboxed environment correctly.
- [ ] Post-purchase / order status page events fire once.

## 7. Server-side tracking (if relevant)

- [ ] Server-side GA4 / GTM server container or Shopify server-side pixel in use? Document it.
- [ ] Client and server events are deduplicated (shared `event_id`/`transaction_id`).
- [ ] Server-side improves resilience to ad blockers/ITP — note the coverage gain and any consent implications.

## 8. Attribution risks

- [ ] UTMs preserved through the journey (incl. into checkout).
- [ ] Cross-domain measurement configured (storefront <-> checkout domain).
- [ ] Consent gaps causing data loss in regulated regions (see consent checklist).
- [ ] Ad-blocker / ITP loss acknowledged; server-side considered if material.
- [ ] Platform discrepancies (GA4 vs Ads vs Meta) explained, not ignored.

## 9. Configuration hygiene

- [ ] Internal traffic / dev stores filtered out.
- [ ] Bot/spam filtering on.
- [ ] Correct time zone & currency in GA4.
- [ ] Key events (conversions) marked in GA4.
- [ ] PII not sent to GA4 (no emails/names in parameters or URLs).
