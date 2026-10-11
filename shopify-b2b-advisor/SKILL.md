---
name: shopify-b2b-advisor
description: Scope and advise on a B2B project on Shopify. Use this when a merchant wants to sell to businesses on Shopify and needs to translate requirements into a realistic architecture and roadmap. Covers customer accounts, company accounts, price lists, private catalog, quote workflow, ERP integration, payment terms, sales reps, order approval, B2B UX, and Shopify Plus vs non-Plus tradeoffs. Produces a requirements analysis, a recommended architecture, a feature matrix, an implementation roadmap, and a risk assessment.
---

# Shopify B2B Advisor

## Short description

A Shopify B2B consultant. It takes a wholesale/B2B ambition and turns it into a grounded plan: what the business actually needs, what Shopify can and can't do natively, where Plus is required, what needs apps or custom work, and how to sequence the build.

## When to use this Skill

Use it when:

- A merchant wants to sell B2B/wholesale on Shopify (alongside or instead of D2C).
- You need to decide between native Shopify B2B (with plan-specific limits), apps, or custom solutions.
- You need a requirements-to-architecture document and a realistic roadmap.
- You're scoping ERP integration, payment terms, or quote/approval workflows.

## Expected inputs

- **Business model**: pure B2B, B2B + D2C, or wholesale arm of a D2C brand.
- **Buyers**: how many companies/buyers, buyer roles, geographies, languages, currencies.
- **Commercial rules**: pricing model (per-company price lists, volume tiers, negotiated), catalog visibility (public vs gated), MOQs, payment terms (net 30/60), tax (B2B tax exemption, VAT).
- **Process**: quoting, order approval chains, sales-rep-assisted ordering, reordering.
- **Systems**: existing ERP/accounting/CRM, current platform, inventory source of truth.
- **Constraints**: current Shopify plan, budget, timeline, internal tech capacity.
- **Goal**: e.g. "launch B2B portal for 200 wholesale accounts with net-30 and tiered pricing".

## Workflow

1. **Clarify requirements.** Use `references/b2b-requirements-framework.md` to capture needs across accounts, pricing, catalog, payments, workflow, integration, and UX. Flag must-haves vs nice-to-haves.
2. **Map needs to current capabilities.** Use `references/shopify-b2b-options.md` and verify each requirement against the official plan comparison, including catalog assignment, payment features and new Shopify Markets eligibility.
3. **Decide the platform tier.** Compare native B2B on the current plan against an upgrade, apps or custom work. Do not assume non-Plus requires wholesale workarounds.
4. **Design the architecture.** Recommend the account model (company accounts vs customer accounts), catalog/pricing structure, payment/terms approach, and the integration pattern with ERP.
5. **Build a feature matrix.** For each required feature: native / app / custom / not feasible, with notes and dependencies.
6. **Plan ERP integration.** Define the source of truth (products, pricing, inventory, orders, customers), sync direction, and method (native, iPaaS/connector, or custom via Admin API), plus failure handling.
7. **Sequence the roadmap.** Phase the build (foundation -> core B2B -> workflow/integration -> optimization) with dependencies.
8. **Assess risk.** Platform fit, integration complexity, data migration, process change, and cost risks.
9. **Assemble the deliverable** using `references/output-templates.md`.

## Quality rules

- Verify plan limits per feature. Native B2B is available on Basic, Grow, Advanced and Plus; direct company/location catalogs and advanced payment features still require Plus. Record the source and check date before recommending an upgrade.
- Separate must-haves from nice-to-haves; don't over-engineer a first launch.
- Prefer native > app > custom, in that order, unless a clear reason justifies otherwise. Flag the long-term maintenance cost of custom and app sprawl.
- For ERP integration, define the source of truth explicitly and handle sync conflicts and failures — this is where B2B projects most often break.
- No destructive recommendations; integrations and migrations must be staged and reversible, with confirmation before touching live data.
- Set realistic timelines and costs; B2B builds are typically larger than D2C. Avoid unrealistic promises.

## Expected outputs

Using `references/output-templates.md`:

1. **Requirements analysis** — needs across all dimensions, prioritized.
2. **Recommended architecture** — account model, pricing/catalog, payments, integration, platform tier.
3. **Feature matrix** — native / app / custom per requirement.
4. **Implementation roadmap** — phased plan with dependencies.
5. **Risk assessment** — risks, likelihood/impact, and mitigations.

## What Pikka adds

This Skill gives you the requirements-to-architecture scoping and a feature matrix to negotiate internally. What it can't do: run discovery workshops with your actual stakeholders, evaluate your specific ERP's integration surface, or build and maintain the Plus/B2B setup once you're committed. [Pikka](https://www.pikka.fr) scopes and implements Shopify B2B projects end to end, including the ERP integration work that's usually where these projects break. Free 30-min review of your scoping doc: `contact@pikka.fr`.

## Reference files to consult

- `references/b2b-requirements-framework.md` — the discovery framework across all B2B dimensions.
- `references/shopify-b2b-options.md` — Shopify B2B capabilities, Plus vs non-Plus, and native/app/custom mapping.
- `references/output-templates.md` — copy-pasteable templates for the deliverable.
