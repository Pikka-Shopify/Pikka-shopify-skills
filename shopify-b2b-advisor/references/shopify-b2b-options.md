# Shopify B2B Options and Capabilities

How to map B2B requirements to what Shopify can actually do. Verify current capabilities and plan boundaries against Shopify's docs, since the platform evolves.

## 1. Verify the plan boundary per feature

Checked 2026-10-11 against Shopify's [official B2B plan comparison](https://help.shopify.com/en/manual/b2b/getting-started/plan-features). Recheck before recommending a plan or implementing: capabilities and store eligibility can change.

Native B2B is available on Basic, Grow, Advanced and Plus. Basic/Grow/Advanced require **new Shopify Markets** for B2B catalog features. Do not treat all native features as Plus-only or assume every feature is available on every plan.

## 2. Native capabilities and limits

| Requirement | Current native capability / limit |
| --- | --- |
| Companies, locations, location-level buyer permissions | Basic, Grow, Advanced and Plus |
| Catalogs assigned to B2B markets | Up to 3 active assignments across all B2B markets on Basic/Grow/Advanced; unlimited on Plus |
| Catalogs assigned directly to companies or locations | Plus only; distinguish negotiated customer-specific catalogs from shared market catalogs |
| Quantity minimums, maximums, increments and price breaks | Basic, Grow, Advanced and Plus |
| Net terms, payment reminders and self-serve reorders | Basic, Grow, Advanced and Plus |
| Deposit requirements, partial payments, payment requests per fulfillment | Plus only |
| Contextual checkout/storefront through Markets | Advanced and Plus |
| Trade theme and quick order lists | Basic, Grow, Advanced and Plus; validate theme implementation |

## 3. Gaps beyond the current plan

Use wholesale apps, custom development, separate stores or manual draft-order quoting only for an identified requirement gap. Compare a plan upgrade against those options, including cost, theme coupling, integration risk and ongoing maintenance. Theme-only hiding is not server-side authorization; verify that any native, app or custom solution enforces private pricing/catalog access across every exposed surface.

## 4. Requirements needing additional verification

Map quoting, buyer-side approval chains, CSV bulk ordering, rep workflows, credit limits, tax handling and ERP integration individually. Native features may cover part of a requirement; do not assume a quick order list supplies CSV upload or a draft-order review supplies a buyer's approval chain. Record native/app/custom coverage, exact plan, prerequisites, remaining gaps, source and check date in the feature matrix.

## 5. ERP integration patterns

- **Define the source of truth per data type** (products, pricing, inventory, customers, orders). The ERP is usually the source for pricing/inventory; Shopify for storefront/checkout.
- **Integration methods:**
  - **Native/marketplace connectors** for common ERPs (fastest, least flexible).
  - **iPaaS / middleware** (e.g. integration platforms) for mapping and orchestration (good balance).
  - **Custom** via Shopify Admin API + webhooks (most flexible, highest build/maintenance).
- **Sync design:** direction, frequency (real-time webhooks vs batch), idempotency, conflict resolution, and failure handling/alerting. This is where B2B projects most often break — design it deliberately and stage it.

## 6. Plan decision checklist

- Confirm the merchant's plan and new Shopify Markets eligibility.
- Separate shared market catalog requirements from direct company/location assignments.
- Check required advanced payment and contextual experience features independently.
- Start with native coverage on the current plan; compare upgrade economics only for real gaps or scale limits.
- Define an upgrade/integration path without assuming wholesale growth automatically requires Plus.
