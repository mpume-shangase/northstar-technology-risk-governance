# Northstar Global — Identity Risk Assessment

> ⚠️ **Constructed case study.** Northstar Global is a fictional organisation created to demonstrate
> assessment methodology. It is not a client, and no real organisational data is represented.

**Role played:** Identity Risk Lead
**Duration modelled:** 6-week assessment
**Frameworks:** NIST CSF 2.0 · ISO/IEC 27001:2022 Annex A · CRISC risk lifecycle

---

## The one-paragraph version

Northstar Global operates a Microsoft 365 E3 estate with Entra ID P1, around 2,000 employees and 300
contractors. I assessed the identity estate against fourteen risk scenarios, scored each on likelihood and
business impact, and found eight breaching the board-approved risk appetite — three of them Critical. I
selected proportionate treatments — Conditional Access with phishing-resistant MFA, PIM with just-in-time
elevation, automated leaver deprovisioning, entitlement management and workload identity governance —
sequenced them into three delivery waves, and re-scored residual risk. Aggregate inherent risk of **202**
reduced to **90**, a **55% reduction**, with zero scenarios remaining above appetite. Delivery cost was
**CAD 148,000** against a modelled single-incident exposure of **CAD 2.1M**.

That paragraph is the interview answer. Everything below is the evidence for it.

---

## Artefacts

| # | Artefact | What it demonstrates |
| --- | --- | --- |
| 1 | [Scope & methodology](./01-scope-and-methodology.md) | Assessment design, evidence sources, control-effectiveness rating, limitations |
| — | [Organisation profile](../../00-programme/organisation-profile.md) | Shared context, identity population, baseline metrics (held in `00-programme/`) |
| 3 | [Risk register — CSV](./03-risk-register.csv) | 14 scenarios, full column set: control effectiveness, framework mapping, owners |
| 4 | [Risk register — readable view](./04-risk-register.md) | Scored register with heat map and residual-risk commentary |
| 5 | [Control-gap assessment](./05-control-gap-assessment.md) | 16 control domains, current vs target maturity, target-state architecture |
| 6 | [Risk acceptance & escalation](./06-risk-acceptance-and-escalation.md) | Acceptance authority matrix, two live acceptances, escalation triggers |
| 7 | [Risk-treatment plan & 90-day recommendations](./07-risk-treatment-plan.md) | Three costed waves, Entra implementation detail, no-cost 90-day option |
| 8 | [Executive summary](./08-executive-summary.md) | One page, board-level, decision-oriented |

![Inherent and residual risk heat map](./assets/risk-heat-map.svg)

---

## Result at a glance

| Measure | Inherent | Residual | Change |
| --- | --- | --- | --- |
| Aggregate risk score (14 scenarios) | 202 | 90 | −55% |
| Scenarios above appetite (≥15) | 8 | 0 | −8 |
| Critical band (20–25) | 3 | 0 | −3 |
| Highest single scenario | 20 | 10 | −50% |
| Permanent Global Administrators | 12 | 2 | −83% |
| Policy-enforced MFA | 0% | 100% | +100pp |
| Median termination-to-disable | 9 days | ≤4 hours | −98% |

## Technical evidence links

Every treatment traces to a lab in this repository. This is the route an IAM interviewer takes; the GRC
interviewer takes the register and executive summary instead.

| Risk | Treatment | Lab |
| --- | --- | --- |
| R-01, R-04 lifecycle | User & Group Lifecycle with PowerShell | Lab 2 (+ IAM-Lifecycle-Automation) |
| R-02, R-10 privileged | Tenant Configuration & Role Management | Lab 1, Lab 9 |
| R-03, R-09 external | External Identities & Cross-Tenant Access | Lab 3 |
| R-01, R-11 hybrid | Hybrid Identity with Entra Connect | Lab 4 |
| R-06 MFA gaps | Authentication Methods, MFA & SSPR | Lab 5 |
| R-07, R-12 | Conditional Access & ID Protection | Lab 6 |
| R-08 workload identities | Workload Identities & Enterprise Apps; App Registrations & Defender for Cloud Apps | Lab 7, Lab 8 |
| R-05, R-13 governance | PIM, Access Reviews & Entitlements | Lab 9 |
| R-14 monitoring | Monitoring, Logs & Identity Secure Score | Lab 10 |

## Residual risk is not zero

Two scenarios remain at Moderate by deliberate decision, both formally accepted with named authority,
monitoring KRI, expiry date and escalation trigger:

- **R-08 (residual 10)** — full workload identity governance requires Workload Identities Premium
  licensing at CAD 68,000, deferred to FY27.
- **R-13 (residual 10)** — 23 pre-existing SoD conflicts cannot clear until the FY27 finance role redesign.

Six of fourteen scenarios retain Impact 5 after treatment. Treatment reduces likelihood; impact rarely
moves. An assessment that treats everything to Low is a sales document, not an assessment.
