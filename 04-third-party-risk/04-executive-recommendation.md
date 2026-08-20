# Executive Recommendation — Cadence Analytics

> ⚠️ Constructed case study. Cadence Analytics is a fictional vendor. See
> [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**To:** Technology Risk Committee
**From:** Technology Risk
**Subject:** Third-party risk assessment — Cadence Analytics (AI demand forecasting)
**Classification:** Internal — Committee

---

## Recommendation

# APPROVE WITH CONDITIONS

Weighted due diligence score **42.6 / 100 — vendor risk rating HIGH.** Approval is recommended subject to
**seven conditions precedent** satisfied before contract signature or any data transfer, and **three
post-contract conditions** delivered to agreed dates.

**Do not sign, and do not transfer data, until conditions CP-1 to CP-7 are evidenced.**

If the vendor declines any of CP-1, CP-2 or CP-5, the recommendation changes to **REJECT**.

## What is being bought and why it matters

Cadence Analytics is an AI-driven demand forecasting platform. Operations proposes it to reduce
finished-goods inventory by an estimated CAD 1.2M annually across six sites. The business case is sound
and this assessment does not dispute it.

To function, the platform ingests three years of order history, inventory positions, pricing and customer
contact records. That is: Northstar's commercial position, and personal data for which Northstar is
controller.

## Assessment summary

![Due diligence scorecard](./assets/vendor-scorecard.svg)

Ten domains assessed against documentary and technical evidence. One rated Adequate, four Gap, two
Significant gap, three **Critical gap**.

Ten vendor-specific risk scenarios were scored: aggregate inherent **139**, with five above the Board
appetite threshold of 15. With all conditions applied, residual falls to **72 — a 48% reduction — with
none above appetite.**

## The three findings that drive the conditions

**1. The vendor's LLM sub-processor may train on Northstar data by default.** *(VR-01, inherent 20 —
Critical)*

Inference runs on a third-party LLM API whose terms permit customer data to be used for model improvement
**unless opt-out is exercised in writing.** Cadence has not exercised it.

Three years of order history, pricing and demand patterns constitute Northstar's commercial position. Once
absorbed into a model serving other customers — including, plausibly, competitors — there is no route to
recall it. This is not a hypothetical: it is the current default configuration.

**2. Sub-processors can be substituted without Northstar's knowledge.** *(VR-02, inherent 16)*

Four sub-processors are disclosed, including the LLM provider and cloud host. The list is not
contractually pinned; Cadence may substitute any of them on 30 days' notice with no approval right for
Northstar. Every assurance in this assessment attaches to entities that can be replaced by ones nobody
has assessed.

**3. The SOC 2 excludes the component we are buying.** *(VR-03, inherent 15)*

Cadence holds ISO 27001 and SOC 2 Type II, and both are genuine. The SOC 2 scope statement explicitly
excludes the AI inference component — the part that processes Northstar's data through a third party.
The certification covers the platform around the risk rather than the risk.

## Conditions precedent — required before signature or data transfer

| # | Condition | Addresses | If refused |
| --- | --- | --- | --- |
| **CP-1** | Written opt-out from LLM model improvement executed and evidenced; contractual prohibition on training use of Northstar data; annual written confirmation | VR-01 | **Reject** |
| **CP-2** | Sub-processor list pinned in contract; substitution requires 60 days notice and Northstar written approval; termination without penalty on reasonable objection | VR-02 | **Reject** |
| **CP-3** | SOC 2 scope extended to include AI inference at next audit cycle; interim independent penetration test of the inference path, at vendor cost, before go-live | VR-03 | Escalate to Committee |
| **CP-4** | Breach notification reduced from 72 to 24 hours from vendor awareness, with defined content requirements | VR-04 | Escalate to Committee |
| **CP-5** | Executed DPA naming Northstar as controller, processing limited to documented instructions, no independent vendor use of personal data | VR-05 | **Reject** |
| **CP-6** | Data export to open format tested and evidenced before go-live; documented conversion path; deletion certificate on termination | VR-07 | Escalate to Committee |
| **CP-7** | Liability cap enhanced for data breach and confidentiality claims; vendor cyber insurance evidenced annually | VR-10 | Escalate to Committee |

## Post-contract conditions

| # | Condition | Addresses | Due |
| --- | --- | --- | --- |
| PC-1 | Just-in-time vendor administrative access with Northstar approval; admin activity logs exposed to Northstar; quarterly review | VR-06 | 90 days |
| PC-2 | Documented manual fallback for demand planning; RTO commitment renegotiated from 8 to 4 hours at first renewal | VR-08 | 60 days |
| PC-3 | Deployment region confirmed and monitored; concentration recorded against TPR-03 in the enterprise register | VR-09 | 30 days |

## Residual risk the Committee is asked to accept

Three scenarios remain at Moderate (10) after all conditions:

- **VR-03** — even with an extended SOC 2 and interim penetration test, the AI inference path carries
  Impact 5 that no assurance activity reduces. Conditions reduce likelihood, not consequence.
- **VR-07** — a tested export reduces the likelihood of being unable to exit; it does not make exiting
  painless. Impact remains 5.
- **VR-09** — Cadence hosts in the same cloud region as Northstar's ERP and identity platform. This
  **compounds TPR-03**, the existing supplier concentration risk already formally accepted under ACC-01.
  Onboarding Cadence makes an accepted risk marginally worse, and the Committee should see that explicitly
  rather than discover it later.

## Why not simply reject

A HIGH rating would justify rejection. It is not recommended, for three reasons.

The business case is real and quantified. Every material gap has a contractual remedy available before
signature — none require the vendor to rebuild its product. And Cadence's underlying security posture is
genuinely reasonable: certified ISMS, tested DR, evidenced penetration testing. **The gaps cluster in AI
governance, sub-processor control and exit — the three areas where the vendor market as a whole is
immature, not where this vendor is unusually weak.**

Rejecting Cadence and selecting an alternative would very likely reproduce the same three gaps with less
leverage to fix them, because Northstar would be later in its own procurement timeline.

The correct response to an immature market is not abstention. It is to convert the gaps into contractual
conditions while leverage exists — which is precisely what happens in the fortnight before signature and
never afterwards.

---

**Decisions requested:** approve subject to CP-1 to CP-7 · note that refusal of CP-1, CP-2 or CP-5
converts this to a rejection · note the compounding effect on accepted risk ACC-01 · assign PC-1 to PC-3
to the Vendor Manager with the dates shown.
