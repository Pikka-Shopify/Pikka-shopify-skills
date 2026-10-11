# Shopify B2B Advisor

> Takes a wholesale ambition and turns it into a grounded plan — including the parts Shopify can't do natively.

This Skill scopes a B2B project on Shopify: what the business actually needs, what's native, where Plus is required, what needs apps or custom work, and how to sequence the build.

## What it's for

- Selling B2B or wholesale on Shopify, alongside or instead of D2C.
- Deciding between native Shopify B2B (with plan-specific limits), apps, or custom development.
- Producing a requirements-to-architecture document and a realistic roadmap.
- Scoping ERP integration, payment terms, or quote and approval workflows.

## What you give it

| | |
|---|---|
| **Business model** | Pure B2B, B2B + D2C, or a wholesale arm of a D2C brand |
| **Buyers** | How many companies and buyers, buyer roles, geographies, languages, currencies |
| **Commercial rules** | Pricing model (per-company price lists, volume tiers, negotiated), catalog visibility, MOQs, payment terms, tax and VAT handling |
| **Process** | Quoting, order approval chains, sales-rep-assisted ordering, reordering |
| **Systems** | Existing ERP, accounting, CRM, current platform, inventory source of truth |
| **Constraints** | Current Shopify plan, budget, timeline, internal tech capacity |
| **Goal** | e.g. "launch a B2B portal for 200 wholesale accounts with net-30 and tiered pricing" |

## What you get back

1. **Requirements analysis** — needs across every dimension, with must-haves separated from nice-to-haves.
2. **Recommended architecture** — account model, pricing and catalog structure, payments, integration pattern, platform tier.
3. **Feature matrix** — native / app / custom / not feasible, per requirement.
4. **Implementation roadmap** — phased plan respecting dependencies.
5. **Risk assessment** — risks, likelihood and impact, and mitigations.

## The honest answer on Shopify Plus

Native B2B is available on Basic, Grow, Advanced and Plus, with feature-specific limits. Company accounts and net terms do not by themselves require Plus. Direct company/location catalogs and advanced payment features do. See the [official plan comparison](https://help.shopify.com/en/manual/b2b/getting-started/plan-features) and verify current store eligibility before choosing architecture.

Prefer native capabilities on the current plan before considering an upgrade, apps or custom development.
The other place B2B projects break is ERP integration. The Skill forces an explicit decision on the source of truth for products, pricing, inventory, orders, and customers — plus sync direction and failure handling — because that ambiguity is what sinks these builds.

## Example prompt

> Use the Shopify B2B advisor Skill. We're a `[D2C brand adding wholesale / pure B2B business]` selling `[what you sell]`. We expect `[number]` company accounts across `[geographies]`, with `[per-company price lists / volume tiers / negotiated pricing]` and `[net-30 / prepayment]` terms. Our ERP is `[name]` and it's the source of truth for `[inventory/pricing/...]`. We're currently on `[Shopify plan]`, budget `[amount]`, target launch `[date]`. Scope this and tell me what's native, what needs apps, and what needs custom work.

## How to use it

New to Skills? The [Getting Started guide](../GETTING-STARTED.md) walks through installation with no coding required. Full details in the [main README](../README.md).

<!--
=======================================================================
BASELINE vs SKILL — comparison section, to fill in after running the test
=======================================================================
Run the same prompt twice: once in a fresh conversation without the Skill,
once with it. Same model, same scenario, no manual editing. Then uncomment
and fill this block, and add the full outputs under examples/.

## What changes when the Skill is enabled?

> Same B2B scenario. Same prompt. Same Claude model. Two independent conversations. No manual editing.

<p align="center">
  <img src="[SCREENSHOT URL]" alt="Claude Code Shopify B2B scoping comparison: without the Skill versus with the Skill" width="100%">
</p>

### At a glance

| | Without the Skill | With the B2B Advisor Skill |
|---|---|---|
| **Output structure** | [...] | [...] |
| **Platform accuracy** | [...] | [...] |
| **Native vs app vs custom** | [...] | [...] |
| **ERP integration** | [...] | [...] |
| **Sequencing** | [...] | [...] |
| **Operational use** | [...] | [...] |

### Same finding, different level of usefulness

<table>
<tr>
<th width="50%">Without the Skill</th>
<th width="50%">With the B2B Advisor Skill</th>
</tr>
<tr>
<td valign="top">

**Recommendation**

> [quote the baseline output]

[why it falls short — e.g. assumes a feature is available without Plus]

</td>
<td valign="top">

**Scoped decision**

> [quote the Skill output]

- Native / app / custom: [...]
- Plan requirement: [...]
- Dependency: [...]

</td>
</tr>
</table>

### Full, unedited outputs

- [Scoping document generated with the B2B Advisor Skill](examples/scoping-with-b2b-skill.md)

<details>
<summary><strong>Comparison methodology</strong></summary>

- Scenario: `[describe]`
- Prompt: `[exact prompt]`
- Model: `[model]`
- Interface: `[Claude Code version / Claude app]`
- Separate, fresh conversations
- No manual correction of either output
- Only intentional difference: the Skill was loaded in the second conversation

This is a single case study, not a scientific benchmark. Results can vary between model runs. The full transcripts are provided so the comparison can be reviewed directly.

</details>
-->

## What Pikka adds

This Skill gives you the requirements-to-architecture scoping and a feature matrix you can negotiate with internally. What it can't do: run discovery workshops with your actual stakeholders, evaluate your specific ERP's integration surface, or build and maintain the Plus/B2B setup once you're committed. [Pikka](https://www.pikka.fr) scopes and implements Shopify B2B projects end to end, including the ERP integration work that's usually where these projects break.

**Free 30-minute review of your scoping doc:** `contact@pikka.fr`
