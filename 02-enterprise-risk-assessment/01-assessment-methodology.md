# Risk Assessment Methodology

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**CRISC Domain 2 — Risk Assessment (22%)**

---

## 1. Objective

Produce a single, aggregatable view of Northstar Global's technology risk exposure that the Technology
Risk Committee can act on — replacing five disconnected registers that could not be summed.

The assessment answers the question the Board asked: *what is our total technology risk exposure, and how
much of it sits above appetite?*

## 2. What this assessment is not

It is not a vulnerability assessment, a penetration test or a control audit. Those produce findings.
This produces **risk scenarios** — statements of how a threat, acting on a weakness, produces a business
consequence.

The distinction is the difference between a technical finding and something a Board can decide on:

| Finding (not a risk) | Risk scenario (assessable) |
| --- | --- |
| "MFA is not enforced." | "If an attacker obtains valid credentials for a finance user, they may authorise fraudulent vendor payments, resulting in direct financial loss and material audit finding." |
| "14 systems are end-of-life." | "If end-of-life systems remain in production without vendor support, security patches may be unavailable when a vulnerability is disclosed." |

A finding has no likelihood and no impact, so it cannot be scored, prioritised or accepted. Registers
full of findings are the most common reason risk reporting fails to influence investment.

## 3. Scenario construction

Every scenario in this register follows the same grammar:

> **If** [threat or event] **acting on** [weakness or condition], **then** [consequence] **resulting in**
> [business impact].

and carries five required attributes:

| Attribute | Why required |
| --- | --- |
| **Business objective threatened** | Ties the risk to something the organisation is trying to achieve. A risk that threatens no objective does not warrant investment. |
| **L1 category** (one only) | Enables aggregation. Assigned where the *primary loss* occurs. |
| **Causal driver** | Recorded separately from category so third-party or internal-control drivers can be analysed without double-counting. |
| **Risk owner** (named individual role) | Accountability for the outcome. |
| **Evidence basis** | What the assessment rests on. Distinguishes tested fact from informed judgement. |

## 4. Scope

**In scope:** all technology risk across six operating countries — cybersecurity, cloud and
infrastructure, data, third-party technology dependencies, emerging technology and AI, technology
operations, resilience, and technology-related regulatory compliance.

**Out of scope:** non-technology operational risk, financial and market risk, and OT process control
networks beyond the IT boundary.

**Known incompleteness:** the technology asset inventory is incomplete, particularly for SaaS acquired
outside IT procurement and AI tooling built on Power Platform. This assessment therefore covers what is
visible. Estimated coverage gap is 12–18%, which is itself tracked as tolerance T-09. An assessment that
does not state what it could not see is asserting completeness it has not earned.

## 5. Evidence sources

Assessment was evidence-led rather than workshop-led. Workshops establish perceived risk; evidence
establishes actual condition, and the two frequently disagree.

| Source | Used for |
| --- | --- |
| Configuration exports — Entra, cloud platform, endpoint management | Control existence and design |
| Vulnerability scan output, 90-day window | CYB-03 likelihood |
| Sign-in and audit logs | CYB-01, CYB-04, EMT-03 |
| Change records, 90-day window | OPS-01 (11 unauthorised changes identified) |
| Backup job records and restore test history | RES-02 |
| Supplier contract and due-diligence files | TPR-01, TPR-02, TPR-03 |
| Network telemetry sampling for AI service destinations | EMT-02 |
| Service catalogue and RTO documentation | RES-01 |
| Structured interviews — Finance, Operations, HR, IT, Compliance | Impact calibration |
| Sector incident benchmarks | Likelihood calibration where internal history was absent |

## 6. Scoring

Likelihood and impact are scored 1–5; inherent score = Likelihood × Impact. Scales, bands and the
Board-approved appetite threshold are defined once in
[`../00-programme/risk-scoring-model.md`](../00-programme/risk-scoring-model.md).

The governing threshold: **no technology risk scoring 15 or above may be retained without formal,
time-boxed acceptance.**

### Impact is business impact

Impact is scored on business consequence, never technical severity. A critical CVSS score on an isolated
test system is a low-impact risk. This is the most frequent scoring error and it systematically
misdirects investment toward whatever the security tooling ranks highest.

### Control effectiveness gates likelihood

Existing controls reduce likelihood **only where tested as effective**:

| Rating | Definition | Effect on scoring |
| --- | --- | --- |
| Effective | Designed correctly, operating consistently, evidence produced | Reduces likelihood |
| Partially effective | Designed correctly, inconsistently applied or unevidenced | **No reduction** |
| Ineffective | Design gap, or not operating | No reduction |
| Absent | No control | No reduction |

Of 24 scenarios, **zero** existing controls were rated Effective. Eleven were Partially effective, twelve
Ineffective, one Absent. A policy that is published but unenforced, a backup that runs but is never
restored, a questionnaire completed at onboarding and never revisited — each of these creates assurance
without creating protection, and each was scored accordingly.

## 7. Inherent, not residual

This register records **inherent risk only**. Residual scoring follows control assessment and treatment
selection in Project 03, because residual risk asserted before controls are tested is an estimate wearing
the costume of a measurement.

The one exception is the [identity deep-dive](./identity-deep-dive/), a completed sub-assessment where
control testing and treatment design were performed and residual risk was measured.

## 8. Aggregation rules

1. One L1 category per scenario, assigned at the point of primary loss.
2. Causal drivers recorded separately — enabling statements like "38% of exposure has an internal control
   weakness driver" without double-counting.
3. Where a detailed sub-assessment exists, its scenarios roll up rather than appearing twice. The identity
   deep-dive's fourteen scenarios contribute to CYB-01, CYB-04 and EMT-03 in this register; they are not
   separately counted in aggregate exposure.
4. Aggregate exposure is the sum of inherent scores. This is a **relative** measure for tracking movement
   and comparing categories, not a statement of expected loss.

## 9. Limitations

- **Point in time.** Configuration drift after fieldwork is not reflected.
- **Likelihood calibration.** Where internal incident history was unavailable, sector benchmarks were
  used. This is weakest for EMT scenarios, where the technology is too new for reliable base rates.
- **Impact estimates** for production disruption were provided by Operations and not independently
  validated.
- **Asset inventory gap** of 12–18% means scenarios exist that this assessment did not identify.
- **Single assessor.** No independent second-line review of the scoring has yet occurred; challenge is
  scheduled at the next Technology Risk Committee.

The last two are the ones that matter. Everything else is normal assessment practice; those two bound
what the register can be relied upon to say.
