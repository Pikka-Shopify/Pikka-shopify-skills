# Output Templates — Shopify Tracking & GA4 Auditor

Copy-pasteable deliverable structure. Fill brackets; delete what doesn't apply.

---

## 1. Measurement diagnosis

> **Current stack.** [How GA4 + ad tags + consent are installed: app / custom pixel / GTM / hardcoded.]
>
> **Trust level.** [Can the numbers be trusted today? Headline issues.]
>
> **Biggest problem.** [The single issue most distorting the data.]

Reconciliation snapshot:

| Source | Purchases (period) | Variance vs Shopify | Note |
| --- | --- | --- | --- |
| Shopify orders | [ ] | baseline | |
| GA4 | [ ] | [ ] | |
| Google Ads | [ ] | [ ] | |
| Meta | [ ] | [ ] | |

---

## 2. Event coverage table

| Event | Present? | Fires once / correct time? | `items` correct? | `currency`+`value`? | Source | Status |
| --- | --- | --- | --- | --- | --- | --- |
| view_item_list | [ ] | [ ] | [ ] | [ ] | [ ] | Pass/Issue |
| view_item | [ ] | [ ] | [ ] | [ ] | [ ] | |
| add_to_cart | [ ] | [ ] | [ ] | [ ] | [ ] | |
| view_cart | [ ] | [ ] | [ ] | [ ] | [ ] | |
| begin_checkout | [ ] | [ ] | [ ] | [ ] | [ ] | |
| add_shipping_info | [ ] | [ ] | [ ] | [ ] | [ ] | |
| add_payment_info | [ ] | [ ] | [ ] | [ ] | [ ] | |
| purchase | [ ] | [ ] | [ ] | [ ] | [ ] | |

---

## 3. Duplicate tracking risks

| # | Duplicate source | Where it happens | Effect | Fix |
| --- | --- | --- | --- | --- |
| 1 | [e.g. GA4 via app + custom pixel] | [ ] | Inflated events/conversions | Keep one source |
| 2 | [thank-you refresh] | purchase | Double purchases | Dedupe on transaction_id |

---

## 4. Consent risks

| # | Risk | Region affected | Compliance / data effect | Fix |
| --- | --- | --- | --- | --- |
| 1 | [ ] | EEA/UK | [ ] | [ ] |

> **Consent Mode v2 status:** [implemented? default denied? linked to Shopify privacy API?]

---

## 5. Recommended tracking plan (target state)

> **Source of truth & ownership.** [Which mechanism owns which platform/event; remove the rest.]

| Event | Owner (tool) | Trigger | Required parameters |
| --- | --- | --- | --- |
| view_item | [ ] | PDP view | currency, value, items |
| add_to_cart | [ ] | add action | currency, value, items |
| begin_checkout | [ ] | checkout start | currency, value, items |
| purchase | [ ] | order complete (once) | transaction_id, currency, value, items; optional: tax, shipping |

> **Consent architecture.** [CMP + Consent Mode v2 + Shopify Customer Privacy API wiring.]
> **Server-side.** [If recommended: what, why, dedup approach.]

---

## 6. QA checklist (validate before trusting)

- [ ] Validate each event in GA4 DebugView / Realtime on a test session.
- [ ] Confirm `purchase` fires once with correct `transaction_id` and `value`.
- [ ] Reconcile GA4 purchases vs Shopify orders for a day/week.
- [ ] Confirm no duplicate GA4/ad events (Tag Assistant / network).
- [ ] Test EEA consent: tags gated pre-consent, fire post-consent.
- [ ] Confirm no PII in parameters/URLs.
- [ ] Verify internal traffic filtered and key events marked as conversions.
