# Risk Treatment Plan

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**CRISC Domain 3 — Risk Response & Reporting**
Treats the 13 above-appetite scenarios from [Project 02](../02-enterprise-risk-assessment/) plus 11
within-appetite scenarios carried for completeness.

---

## Sequencing logic

Waves are ordered by **risk reduction per dollar per week**, not by risk score.

EMT-03 is Critical but its full remediation needs licensing that isn't funded, so only its inventory
component sits in Wave 1. C-23 (backup restore testing) addresses a Moderate scenario and sits in Wave 1
anyway, because the control is already designed, costs nothing but scheduling, and every resilience claim
in the register depends on it being true.

| Wave | Theme | Weeks | Scenarios | Exposure reduced | Cost (CAD) |
| --- | --- | --- | :-: | --- | --- |
| 1 | Close what is open and free | 1–10 | 8 | 129 → 58 | 84,000 |
| 2 | Build what is missing | 11–22 | 9 | 122 → 68 | 218,000 |
| 3 | Systematise and evidence | 23–36 | 7 | 79 → 43 | 96,000 |
| | **Total** | **36 weeks** | **24** | **330 → 169** | **398,000** |

## Wave 1 — Close what is open and free (weeks 1–10)

**Rationale:** four controls are correctly designed and simply not operating. Fixing those requires
enforcement and ownership, not procurement. This wave delivers 44% of total risk reduction for 21% of
total cost.

| Action | Issue | Controls | Scenarios |
| --- | --- | --- | --- |
| Enforce MFA via Conditional Access — report-only, then enforce; remediate 4 dependent service accounts | ISS-03 | C-01 | CYB-01, CYB-05 |
| Mandate phishing-resistant methods for privileged roles and finance | ISS-03 | C-02 | CYB-01, CYB-04 |
| Convert 68 standing privileged assignments to eligible with approval and 4-hour limit | ISS-04 | C-03 | CYB-04 |
| Clear the 34 overdue critical vulnerabilities; automate SLA escalation at 75% elapsed | ISS-01 | C-05 | CYB-03 |
| Perform full restore test per critical service; establish quarterly cycle | ISS-02 | C-23 | RES-02 |
| Block unapproved external AI services at egress; provide sanctioned alternative | ISS-06 | C-18 | EMT-02 |
| Mandatory AI system registration — named owner and authority boundary or no deployment | ISS-07 | C-17 | EMT-01, EMT-03 |
| Inventory all 340 workload identities with owner and justification | ISS-05 | C-19 | EMT-03 |

**Exit criteria:** policy-enforced MFA 100% · permanent Global Administrators = 2 · critical vulnerabilities
past SLA = 0 · restore tested for all 9 critical services · unapproved AI service traffic = 0 · AI systems
registered = 100% · workload identity inventory = 100% with owners.

### Sequencing note

Report-only mode runs a minimum of 10 business days before MFA enforcement. This is not caution for its
own sake — a tenant with 145 service accounts and 300 contractors has unknown authentication dependencies,
and enforcing without the report-only pass is how identity programmes cause a Monday morning outage in a
plant running 24 hours. Rollout is ringed: IT pilot, corporate, plant, contractors.

## Wave 2 — Build what is missing (weeks 11–22)

**Rationale:** eleven controls are absent and must be built. This is where the money goes.

| Action | Issue | Controls | Scenarios |
| --- | --- | --- | --- |
| Deploy continuous cloud configuration compliance scanning with auto-remediation | ISS-10 | C-09 | CLD-01 |
| Build data inventory; apply technical retention enforcement | ISS-11 | C-12 | DAT-01 |
| Extend region restrictions to remaining 3 platforms | ISS-12 | C-13 | DAT-02 |
| Establish supplier reassessment cycle; map subcontractors; add 24-hour notification clauses | ISS-13 | C-15 | TPR-01, TPR-02 |
| Document manual fallback for order processing; exit plan per critical supplier | ISS-14 | C-16 | TPR-01, TPR-03 |
| Complete EDR deployment to 100% of endpoints | ISS-08 | C-06 | CYB-02 |
| Quarterly phishing simulation with targeted follow-up training | — | C-08 | CYB-05 |
| Extend change control to standard changes; alert on out-of-process change | ISS-15 | C-21 | OPS-01 |
| Embed regulatory notification triggers and statutory timers in incident workflow | ISS-18 | C-24 | REG-01 |
| Define RTO for all 9 critical services; schedule end-to-end recovery test | ISS-17 | C-10 | RES-01, CLD-02 |

**Exit criteria:** cloud configuration compliance ≥95% · data inventory complete for personal data ·
region restrictions on 5 of 5 platforms · 11 of 11 critical suppliers reassessed with subcontractors
mapped · EDR coverage 100% · unauthorised changes = 0 · RTO defined for all critical services.

## Wave 3 — Systematise and evidence (weeks 23–36)

**Rationale:** converts one-off remediation into repeatable, evidenced control operation — which is what
customers and auditors actually ask for.

| Action | Issue | Controls | Scenarios |
| --- | --- | --- | --- |
| SoD conflict matrix defined; quarterly detective reporting to CFO and Internal Audit | ISS-20 | C-04 | CYB-01 |
| Automated master data validation before period-end reporting | — | C-14 | DAT-03 |
| Cloud budget alerting and quota enforcement per subscription | — | C-11 | CLD-03 |
| Mandatory documented human review for consequential AI output | — | C-20 | EMT-04 |
| Extend lifecycle tracking beyond servers; remediate 14 EOL systems | ISS-16 | C-22 | OPS-02 |
| Central control evidence repository maintained by second line | ISS-19 | C-25 | REG-02 |
| Cross-region failover tested for the 6 untested critical services | ISS-17 | C-10 | CLD-02, RES-01 |

**Exit criteria:** SoD reporting operating quarterly · EOL systems remediated or formally accepted ·
evidence repository populated for all 25 controls · failover tested for 9 of 9 critical services.

---

## Formal risk acceptances

Five residual positions are recommended for acceptance rather than further treatment. Each carries a named
authority, compensating controls, a monitoring KRI, an expiry date and hard escalation triggers, per the
[appetite statement](../01-governance-framework/02-risk-appetite-and-tolerance.md).

| Ref | Risk | Residual | Authority | Why accepted | Expiry |
| --- | --- | :-: | --- | --- | --- |
| **ACC-01** | TPR-03 — supplier concentration | 10 | Procurement Director | Diversifying ERP, identity and email across providers would cost more than the exposure and introduce integration risk of its own. Concentration is measured and reported; exit plans documented. | 12 months |
| **ACC-02** | CYB-02 — ransomware to plant | 10 | CISO | IT/OT segmentation at the two largest plants requires CAD 340,000 of capital investment, deferred to FY27. Compensating: EDR at 100%, restore testing, monitoring. | 6 months |
| **ACC-03** | TPR-01, TPR-02 — supplier failure and breach | 10 | Procurement Director | Due diligence and contractual controls reduce likelihood; they cannot reduce impact. A supplier failure remains materially disruptive regardless of how well it was assessed. | 6 months |
| **ACC-04** | EMT-03 — workload identity governance | 10 | CIO | Full lifecycle governance for workload identities requires additional licensing at CAD 68,000 annually, deferred to FY27. Partial treatment reduces the scenario from Critical to Moderate at no licence cost. | 6 months |
| **ACC-05** | RES-01 — recovery exceeds tolerance | 10 | COO | RTO definition and annual testing reduce likelihood. Meeting the maximum tolerable disruption for order processing requires platform investment scheduled for FY27. | 6 months |

**The pattern in four of five is the same:** treatment reduces likelihood, and impact is unchanged because
nothing in the treatment makes the consequence smaller. That is the honest position, and it is why every
one of these lands at 10 rather than in the Low band.

Being able to say *"I chose to carry this one, here is the authority, the compensating control, the
threshold that would change my mind, and the date it expires"* is a materially stronger answer than
claiming everything was fixed.

## Costs

| Item | Cost (CAD) |
| --- | --- |
| Entra ID Governance add-on (2,000 users, annual) | 62,000 |
| Cloud security posture management tooling | 48,000 |
| Data discovery and retention enforcement platform | 74,000 |
| AI egress control and monitoring | 26,000 |
| EDR licence extension to remaining endpoints | 18,000 |
| Internal effort — Technology Risk, 1.0 FTE × 36 weeks | 92,000 |
| Internal effort — distributed control owners | 48,000 |
| External specialist support — PIM, SoD, supplier framework | 30,000 |
| **Total** | **398,000** |
| *Deferred to FY27* | *408,000* |

*Deferred: IT/OT segmentation 340,000 · Workload Identities Premium 68,000.*

### Commercial case

Modelled single-incident exposure across the three Critical scenarios — fraudulent payment, production
halt, or confidential data disclosure through an unapproved AI service — is **CAD 2.4M**, comprising
direct loss, response and forensics, production disruption, regulatory cost and customer contract
remediation.

At a modelled 35% annual likelihood of at least one materialising before treatment, expected annual loss
is approximately **CAD 840,000** against a treatment cost of CAD 398,000. The programme pays for itself if
it prevents one incident within five years.

This is a model, not a fact, and it is presented to the Committee as such. Quantification exists to make
the trade-off discussable, not to claim precision that does not exist.

## 90-day position

If the Committee funds nothing else, Wave 1 alone reduces aggregate exposure from **330 to 259 — a 22%
reduction** — and clears five of the 13 above-appetite scenarios. Four of its eight actions require no
capital expenditure at all, because they fix controls that were designed correctly and never operated.

The correct response to "we cannot fund the full programme this year" is a shorter list, not a rejected
business case.
