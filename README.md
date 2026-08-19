# Northstar Identity Governance & Risk

**Identity & Access Management · Identity Governance · Cybersecurity Risk · PMP**

A four-project programme showing the full arc from identity risk assessment through control design,
implementation, project delivery and executive reporting. Technical configuration lives in the companion
repositories: **[SC-300-Lab-Series](https://github.com/mpume-shangase/SC-300-Lab-Series)** and
**[IAM-Lifecycle-Automation](https://github.com/mpume-shangase/IAM-Lifecycle-Automation)**.

> ⚠️ **Northstar Global is a constructed case study, not a client engagement.** No real organisation,
> engagement or data is represented. See [`00-programme/disclaimer.md`](./00-programme/disclaimer.md).

---

## What this repository is for

The lab repository proves I can configure Microsoft Entra. This one proves I can decide what should be
configured, why, at what cost, and how the residual risk gets reported to the people accountable for it.

| Before | After |
| --- | --- |
| "I know how to configure Conditional Access." | "I identified an unacceptable authentication risk, assessed likelihood and business impact, selected Conditional Access and MFA as risk-treatment controls, implemented them, measured the residual risk, and reported the outcome to stakeholders." |

## Start here

**Hiring for GRC, risk or governance?** Read the
[executive summary](./01-risk-assessment/08-executive-summary.md) — one page — then the
[risk register](./01-risk-assessment/04-risk-register.md) and the
[acceptance and escalation process](./01-risk-assessment/06-risk-acceptance-and-escalation.md).
Roughly 15 minutes.

**Hiring for IAM engineering?** Read the [treatment plan](./01-risk-assessment/07-risk-treatment-plan.md),
which maps each risk to its Entra implementation, then follow the lab links into the configuration itself.
Roughly 15 minutes.

**Recruiter with 3 minutes?** The executive summary alone.

---

## Programme structure

```
northstar-identity-governance/
├── 00-programme/              Shared across all four projects - defined once
│   ├── organisation-profile.md    Northstar context, identity population, baselines
│   ├── risk-scoring-model.md      Scales, bands, board-approved appetite statement
│   ├── kri-catalogue.md           14 KRIs with thresholds and sources
│   ├── glossary.md                Risk, identity and Entra terminology
│   └── disclaimer.md              What is constructed and what is real
│
├── 01-risk-assessment/        Phase 1 - Assess
├── 02-jml-transformation/     Phase 2 - Transform
├── 03-privileged-access/      Phase 3 - Secure
└── 04-access-certification/   Phase 4 - Govern
```

Anything referenced by more than one project lives in `00-programme/` and nowhere else. Organisation
headcount, risk bands and KRI identifiers appear once, so the register in project 01 and the dashboard in
project 04 cannot drift apart.

## The four projects

| Phase | Project | Risk origin | Outcome | Status |
| --- | --- | --- | --- | --- |
| 1 · Assess | [Identity Risk Assessment](./01-risk-assessment/) | — | 14 scenarios scored; aggregate risk 202 → 90 (−55%); 8 above-appetite scenarios cleared | **Complete** |
| 2 · Transform | [Joiner–Mover–Leaver Transformation](./02-jml-transformation/) | R-01, R-03, R-04 | Termination-to-disable 9 days → ≤4 hours | Scaffolded |
| 3 · Secure | [Privileged Access Risk Reduction](./03-privileged-access/) | R-02, R-10 | Standing privileged assignments 68 → 2 | Scaffolded |
| 4 · Govern | [Access Certification Program](./04-access-certification/) | R-05, R-09, R-13 | 0 → 4 Tier 1 applications under quarterly certification | Scaffolded |

Each project opens with an explicit risk-to-project chain: what was found, what it scored, whether it
breached appetite, what treatment was selected, what the residual position became, and who it was reported
to. Projects 2–4 exist because the assessment found something, not because the capability is interesting.

![Inherent and residual risk heat map](./01-risk-assessment/assets/risk-heat-map.svg)

## Technical evidence

Every treatment traces to a lab in **[SC-300-Lab-Series](https://github.com/mpume-shangase/SC-300-Lab-Series)**
(all 10 complete) or to **[IAM-Lifecycle-Automation](https://github.com/mpume-shangase/IAM-Lifecycle-Automation)**,
a working PowerShell + Microsoft Graph JML pipeline with certificate auth, dry-run mode and audit logging.

| Risk | Treatment | Technical evidence |
| --- | --- | --- |
| R-01, R-04 | HR-driven lifecycle, automated leaver deprovisioning, mover recalculation | Lab 2 — User & Group Lifecycle with PowerShell · **IAM-Lifecycle-Automation** |
| R-02, R-10 | PIM eligible assignments, tiering, break-glass design | Lab 1 — Tenant Configuration & Role Management · Lab 9 |
| R-03, R-09 | Non-employee and guest governance, sponsor + expiry | Lab 3 — External Identities & Cross-Tenant Access · Lab 9 |
| R-01, R-11 | Hybrid identity, on-prem AD as sync source, service account migration | Lab 4 — Hybrid Identity with Entra Connect |
| R-06 | MFA enforcement, phishing-resistant methods, SSPR | Lab 5 — Authentication Methods, MFA & SSPR |
| R-07, R-12 | Block legacy auth, device compliance grant controls, risk-based policy | Lab 6 — Conditional Access & ID Protection |
| **R-08** | **Workload identity inventory, ownership, least-privilege Graph permissions** | **Lab 7 — Workload Identities & Enterprise Apps · Lab 8 — App Registrations & Defender for Cloud Apps** |
| R-11 | Managed identities, workload identity federation | Lab 7 — Workload Identities & Enterprise Apps |
| R-05, R-13 | Access certification, entitlement management, SoD enforcement | Lab 9 — Identity Governance: PIM, Access Reviews & Entitlements |
| R-14 | Log routing, retention, KRI workbooks, Secure Score baseline | Lab 10 — Monitoring, Logs & Identity Secure Score |

All ten labs are mapped. R-08 — the highest-scoring scenario in the assessment — is backed by two labs
plus Defender for Cloud Apps, which is the strongest evidence chain in this portfolio.

## Frameworks referenced

NIST Cybersecurity Framework 2.0 · ISO/IEC 27001:2022 Annex A (5.15–5.18, 8.2, 8.5, 8.15) ·
ISACA CRISC risk lifecycle · PMBOK · Microsoft Zero Trust and Entra ID Governance capability model

## Conventions

- Folders are numbered to force reading order; GitHub sorts alphabetically and will not infer it.
- Risk IDs (`R-01`…`R-14`), KRI IDs (`KRI-01`…`KRI-14`) and acceptance IDs (`ACC-01`, `ACC-02`) are stable
  across the whole programme and safe to cite in an interview.
- Every artefact carries the constructed-case-study notice within its first three lines.
- Registers are held as CSV with a rendered markdown view alongside, so the data is readable on GitHub and
  usable in a spreadsheet.

## Licence

Artefacts CC BY 4.0, code MIT. See [`LICENSE`](./LICENSE).
