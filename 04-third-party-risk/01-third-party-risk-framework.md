# Third-Party Technology Risk Framework

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**CRISC Domains 2 and 3 — Risk Assessment · Risk Response & Reporting**

---

## 1. Why this framework exists

[Project 02](../02-enterprise-risk-assessment/) identified three third-party scenarios carrying 40 points
of inherent exposure, two of them above appetite. [Project 03](../03-control-assessment-treatment/)
tested the controls meant to address them and rated both Ineffective: supplier due diligence happens at
onboarding only, with no reassessment cycle and no subcontractor mapping across all eleven critical
suppliers (ISS-13), and no contingency or exit plan exists for any of them (ISS-14).

This framework fixes the method, and then applies it to a live onboarding decision.

## 2. Supplier tiering

Due diligence effort is proportionate to exposure, not to contract value. A CAD 40,000 SaaS holding
customer personal data warrants more scrutiny than a CAD 400,000 hardware supplier holding none.

| Tier | Criteria (any one triggers) | Due diligence | Reassessment |
| --- | --- | --- | --- |
| **Critical** | Processes personal or regulated data · supports a process with a maximum tolerable disruption under 8 hours · holds privileged access to Northstar systems · uses AI on Northstar data | Full 10-domain assessment, evidence-backed, executive decision | Annual |
| **High** | Processes confidential commercial data · integrated to a core system · single source for a business-critical function | 10-domain assessment, questionnaire plus certification review | Every 2 years |
| **Standard** | No sensitive data, no system integration, substitutable | Questionnaire and certification review | Every 3 years |

**Tier is assigned at onboarding and re-tested at each renewal.** A supplier's tier moves when its scope
moves — the most common failure in vendor risk is a Standard supplier acquiring data access through scope
creep and never being re-tiered.

## 3. Assessment domains and weighting

Weights reflect where third-party incidents actually originate for Northstar's profile, not an even
split across a checklist.

| Domain | Weight | Why weighted here |
| --- | :-: | --- |
| Data protection and privacy | 15% | Northstar is controller; regulatory consequence is non-transferable |
| AI and model governance | 15% | Emerging exposure with no established control practice; Board appetite is bounded, and the bounds must be testable |
| Subcontractor and fourth-party management | 12% | The party you assessed is rarely the only party holding your data |
| Information security governance | 10% | Foundation for everything else |
| Access control and authentication | 10% | Vendor access is privileged access |
| Resilience and business continuity | 10% | Order-adjacent systems carry a 4-hour tolerance |
| Incident management and notification | 8% | Determines whether Northstar can meet its own regulatory clock |
| Contractual controls | 8% | The only mechanism that survives a relationship turning adversarial |
| Compliance and certification | 6% | Useful evidence, but scope-limited — see below |
| Exit and data portability | 6% | Cheap to require at onboarding, near-impossible to obtain later |

### On certifications

A SOC 2 or ISO 27001 certificate is evidence, not an answer. **The question is always what the scope
statement excludes.** Certifications are commonly held by the corporate entity or the core platform while
the newest component — usually the one you are actually buying — sits outside the audit boundary. Reading
the scope statement takes five minutes and is the highest-yield activity in vendor assessment.

## 4. Scoring

Each domain scores 0–5 against evidence, weighted, and summed to 100.

| Score | Meaning |
| --- | --- |
| 5 | Control present, evidenced, independently assured |
| 4 | Control present and evidenced |
| 3 | Control present, partially evidenced or partially scoped |
| 2 | Control asserted, weakly evidenced, or materially gapped |
| 1 | Control absent or contradicted by evidence |
| 0 | Vendor unable or unwilling to respond |

| Weighted score | Vendor risk rating | Decision posture |
| --- | --- | --- |
| 80–100 | Low | Approve |
| 60–79 | Moderate | Approve, with conditions tracked post-contract |
| 40–59 | **High** | Approve only with conditions precedent, or reject |
| Below 40 | Critical | Reject, or escalate to Technology Risk Committee for exception |

## 5. Conditions precedent vs post-contract

This distinction is the practical core of the framework.

| | Definition | Applied when |
| --- | --- | --- |
| **Condition precedent** | Must be satisfied **before** contract signature or data transfer, whichever is earlier | The risk materialises on day one, or leverage disappears after signature |
| **Post-contract condition** | Committed contractually, delivered to an agreed date after signature | The risk builds over time and the remedy takes time to implement |

**Commercial leverage is at its maximum immediately before signature and collapses immediately after.**
Anything genuinely required should be a condition precedent. A vendor who will not commit before signing
will not prioritise it afterwards, when the only remaining remedy is termination — which Northstar will
not exercise over a control gap once the platform is embedded in business process.

## 6. Assessment evidence standard

Questionnaire responses are claims. Each domain requires at least one of:

- Independent assurance report with the **scope statement read**, not just the opinion
- Contractual commitment in executable form
- Configuration or technical evidence demonstrable in a live session
- Test evidence with dates and results, not policy documents describing intent

Where only a questionnaire response exists, the domain scores no higher than 2.

## 7. Application

This framework is applied to a live onboarding decision in
[`02-due-diligence-assessment.csv`](./02-due-diligence-assessment.csv) and
[`03-vendor-risk-register.csv`](./03-vendor-risk-register.csv), with the recommendation to the Technology
Risk Committee in [`04-executive-recommendation.md`](./04-executive-recommendation.md).
