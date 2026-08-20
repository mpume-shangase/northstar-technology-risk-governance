# 07 — Risk-Treatment Plan & 90-Day Recommendations

> ⚠️ Constructed case study. Northstar Global is fictional.

## Treatment option selection

Each scenario was assessed against the four standard responses before a treatment was designed. Selecting
"mitigate" for everything without considering the alternatives is the most common weakness in identity
risk assessments, because it produces a plan that is technically sound and commercially unapprovable.

| Option | Applied to | Rationale |
| --- | --- | --- |
| **Avoid** | None | No scenario could be removed by ceasing the underlying activity. Northstar cannot stop employing contractors or stop using SAP. |
| **Transfer** | Partially, R-01/R-13 | Cyber insurance covers financial loss but transfers no regulatory or operational consequence. Treated as a financial backstop, not a control. |
| **Accept** | R-08 (partial), R-13 (partial) | Documented in [`06-risk-acceptance-and-escalation.md`](./06-risk-acceptance-and-escalation.md) with named authority, KRI and expiry. |
| **Mitigate** | All 14 | Primary response. Sequenced below. |

## Sequencing logic

Waves are ordered by **risk reduction per dollar per week**, not by risk score. R-08 is a Critical
scenario but sits in Wave 3, because its treatment depends on an inventory that does not yet exist and its
full remediation needs licensing that is not yet funded. R-07 is one band lower but sits in Wave 1,
because blocking legacy authentication takes one Conditional Access policy and removes an entire
authentication bypass path.

| Wave | Theme | Weeks | Scenarios | Inherent → Residual | Cost (CAD) |
| --- | --- | --- | --- | --- | --- |
| 1 | Close the authentication bypass | 1–8 | R-06, R-07, R-02, R-10, R-14 | 71 → 24 | 42,000 |
| 2 | Fix the lifecycle | 9–20 | R-01, R-03, R-04, R-12 | 60 → 23 | 61,000 |
| 3 | Govern what remains | 21–36 | R-05, R-09, R-11, R-13, R-08 | 71 → 43 | 45,000 |
| | **Total** | **36 weeks** | **14** | **202 → 90** | **148,000** |

## Wave 1 — Close the authentication bypass (weeks 1–8)

**Rationale:** Every other control is theatre while a credential-only path to finance data exists. This
wave delivers 42% of total risk reduction for 28% of the cost.

| # | Action | Scenario | Entra implementation | Evidence |
| --- | --- | --- | --- | --- |
| 1.1 | Analyse 90 days of legacy authentication sign-ins; remediate the 4 dependent service accounts | R-07 | Sign-in log workbook filtered on legacy client apps | Lab 10 |
| 1.2 | Deploy Conditional Access in report-only, then enforce: MFA for all users, all cloud apps | R-06 | Conditional Access policy, report-only → on | Labs 5, 6 |
| 1.3 | Block legacy authentication | R-07 | Conditional Access, block legacy clients | Lab 6 |
| 1.4 | Mandate phishing-resistant MFA for all privileged roles and Finance | R-06 | Authentication Strengths + Authentication Methods policy | Lab 5 |
| 1.5 | Define and provision two break-glass accounts; FIDO2 keys to physical custody; alerting on any sign-in; CA exclusion documented | R-10 | Cloud-only accounts, CA exclusion, Log Analytics alert rule | Labs 9, 10 |
| 1.6 | Onboard PIM: convert 68 standing assignments to eligible, with approval, justification, MFA on activation, 4-hour maximum | R-02 | Privileged Identity Management | Lab 9 |
| 1.7 | Route sign-in, audit and provisioning logs to Log Analytics with 12-month retention; build KRI workbook | R-14 | Diagnostic settings, Log Analytics workspace | Lab 10 |

**Wave 1 exit criteria:** legacy auth sign-ins = 0 · policy-enforced MFA = 100% of active users ·
permanent Global Administrators = 2 · break-glass tested and evidenced · 12-month log retention live ·
KRI-01 to KRI-14 collecting.

### Sequencing note on 1.2

Report-only mode runs for a minimum of 10 business days before enforcement. This is not caution for its
own sake — a tenant with 145 service accounts and 300 contractors will have unknown authentication
dependencies, and enforcing MFA without the report-only pass is how identity projects cause a Monday
morning outage in a plant that runs 24 hours. The rollout is ringed: IT pilot, then corporate, then plant,
then contractors.

## Wave 2 — Fix the lifecycle (weeks 9–20)

**Rationale:** Wave 1 stops the front door. Wave 2 stops access outliving the person.

| # | Action | Scenario | Entra implementation | Evidence |
| --- | --- | --- | --- | --- |
| 2.1 | Establish HR as source of authority; map attributes; agree data quality standard | R-01, R-04 | HR-driven provisioning (Dynamics 365 HR → Entra) | Lab 2 |
| 2.2 | Build joiner workflow: pre-hire account, birthright access by dynamic group | R-04 | Lifecycle Workflows + dynamic groups | Lab 2 |
| 2.3 | Build leaver workflow: same-day disable, session revocation, manager notification, 30-day retention then delete | R-01 | Lifecycle Workflows | Lab 2 |
| 2.4 | Build mover workflow: recalculate role-based access, manager re-certification of retained entitlements within 10 days | R-04 | Lifecycle Workflows + Access Reviews | Labs 2, 9 |
| 2.5 | Non-employee onboarding via access package: mandatory sponsor, mandatory expiry, 14-day re-attestation | R-03 | Entitlement Management | Lab 9 |
| 2.6 | Enforce device compliance for Tier 1 applications; scoped exception path for partner access | R-12 | Conditional Access device compliance grant | Lab 6 |

**Wave 2 exit criteria:** median termination-to-disable ≤ 4 hours · terminated accounts enabled >24h = 0 ·
contractor identities with expiry = 100% · mover recertification completing within 10 days · Tier 1 access
from non-compliant devices = 0.

## Wave 3 — Govern what remains (weeks 21–36)

**Rationale:** Waves 1 and 2 fix the mechanics. Wave 3 builds the evidence machine that satisfies auditors
and customers, and addresses the non-human identity population.

| # | Action | Scenario | Entra implementation | Evidence |
| --- | --- | --- | --- | --- |
| 3.1 | Classify applications into Tier 1/2/3; assign named application owners | R-05 | Application inventory | Lab 9 |
| 3.2 | Quarterly access certification for Tier 1; auto-revoke on non-response; exception register | R-05 | Access Reviews | Lab 9 |
| 3.3 | Guest governance: access packages with sponsor and expiry; semi-annual review; auto-remove dormant >90 days | R-09 | Entitlement Management + Access Reviews for guests | Lab 9 |
| 3.4 | Inventory all 340 workload identities; assign owner and business justification; revoke unused permissions to least privilege | R-08 | App registration audit, Graph permission enumeration | Labs 6, 10 |
| 3.5 | Migrate service accounts to managed identity or workload identity federation where supported; vault + rotate the remainder | R-11 | Managed Identities, Workload Identity Federation | Lab 6 |
| 3.6 | Define finance SoD conflict matrix; encode as mutually exclusive access packages; quarterly detective reporting | R-13 | Entitlement Management separation of duties | Lab 9 |

**Wave 3 exit criteria:** 4 of 4 Tier 1 applications certified · reviewer response ≥90% · workload identity
inventory 100% with named owners · SoD matrix live and violations reported · Identity Secure Score ≥79%.

## Cost breakdown

| Item | Cost (CAD) | Note |
| --- | --- | --- |
| Entra ID Governance add-on (2,000 users, annual) | 62,000 | Required for Lifecycle Workflows, Entitlement Management, Access Reviews |
| Internal effort — IAM Lead, 0.8 FTE × 36 weeks | 48,000 | Existing headcount, allocated |
| Internal effort — application owners, HR, Finance | 18,000 | Distributed, ~2 hrs/week each |
| External specialist support — PIM and SoD design | 20,000 | 12 days |
| **Total** | **148,000** | |
| *Deferred to FY27* | *68,000* | *Workload Identities Premium — see ACC-01* |

### Cost justification

Modelled single-incident exposure for a business email compromise leading to fraudulent payment release —
the scenario R-01, R-06 and R-13 collectively enable — is **CAD 2.1M**, based on: average fraudulent
payment CAD 340K, incident response and forensics CAD 280K, four days of partial production disruption
CAD 900K, regulatory and notification costs CAD 180K, and customer contract remediation CAD 400K.

At a 30% modelled annual likelihood of at least one identity-driven incident before treatment, expected
annual loss is approximately CAD 630K against a treatment cost of CAD 148K. The programme pays for itself
if it prevents one incident in four years.

This number is a model, not a fact, and it is presented to the committee as such. The purpose of
quantifying is to make the trade-off discussable, not to pretend to precision that does not exist.

## 90-day remediation recommendations

If the committee funds nothing else, these five actions in 90 days deliver the majority of the available
risk reduction. Ordered by effort-to-impact.

| Priority | Action | Effort | Risk reduction | Cost |
| --- | --- | --- | --- | --- |
| 1 | Enforce MFA by Conditional Access for all users (report-only first) | Low | R-06: 20 → 5 | Nil |
| 2 | Block legacy authentication | Low | R-07: 16 → 4 | Nil |
| 3 | Onboard PIM; reduce permanent Global Admins from 12 to 2 | Medium | R-02: 15 → 5 | Nil (P2 trial, then licensed) |
| 4 | Disable the 34 terminated accounts still active; implement interim daily HR reconciliation report pending automation | Low | R-01: 20 → 10 interim | Nil |
| 5 | Set expiry dates on all 300 contractor identities; assign sponsors | Medium | R-03: 16 → 10 interim | Nil |

**These five actions cost nothing beyond internal effort and reduce aggregate risk from 202 to 128 — a
37% reduction with no capital expenditure.** They are separated deliberately, because the correct answer
to "we cannot fund the programme this year" is a shorter list, not a rejected business case.

Items 4 and 5 are marked *interim* because a daily reconciliation report is a person doing a machine's
job. It reduces likelihood from 4 to 3, not to 1. Full treatment requires the Wave 2 automation, and the
register reflects the interim position honestly rather than claiming the automated residual early.
