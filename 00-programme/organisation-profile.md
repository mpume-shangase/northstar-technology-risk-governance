# Organisation Profile — Northstar Global

> ⚠️ Constructed case study. See [`disclaimer.md`](./disclaimer.md).
>
> **Canonical source.** These figures are referenced by all four projects. Change them here only.

## Organisation profile

| Attribute | Detail |
| --- | --- |
| Sector | Manufacturing & distribution |
| Employees | ~2,000 across 6 countries (Canada, US, Mexico, UK, Poland, Malaysia) |
| Non-employees | ~300 contractors, ~90 external partner guests |
| Growth context | Two acquisitions in 36 months; headcount up 40% with no corresponding investment in identity process |
| Regulatory drivers | PIPEDA, SOX-equivalent internal financial controls, customer security questionnaires as a condition of tier-1 supply contracts |

The growth context is the root cause behind most of the register. Northstar did not make bad identity
decisions; it made reasonable decisions for a 1,400-person company and never revisited them at 2,000.
Manual leaver processing works at 15 departures a month and fails at 45.

## Business units and access sensitivity

| Function | Headcount | Critical systems | Why access matters here |
| --- | --- | --- | --- |
| Finance | 90 | SAP S/4HANA, banking portal | Payment release, vendor master data — SoD exposure |
| HR | 35 | Dynamics 365 HR module | Personal data of all staff; source of authority for lifecycle |
| Sales | 340 | Dynamics 365 Sales | Customer data, pricing, pipeline |
| Operations / Plant | 1,200 | Quality system (SharePoint), OT historian front end | Production continuity; largest contractor population |
| IT | 85 | Entra, Azure, on-prem AD | Privileged access concentration |
| Executive | 12 | All of the above | High-value phishing targets |

## Identity environment

| Layer | Current state |
| --- | --- |
| Directory | Entra ID P1; hybrid identity via Entra Connect; on-premises AD retained as authoritative for plant systems |
| Productivity | Microsoft 365 E3 |
| Endpoint | Intune deployed to ~80% of corporate devices; compliance not enforced as an access condition |
| Authentication | Per-user MFA on ~70% of employees; Microsoft Authenticator and SMS both permitted; no authentication strength policies |
| Authorisation | Security-group based; ~1,900 groups, of which ~600 have no owner recorded |
| Privileged access | Standing assignments: 12 Global Administrators, 22 Privileged Role Administrators, 18 Exchange Administrators, 16 Application Administrators. No PIM. |
| Lifecycle | HR email → service desk ticket → manual account creation → manager requests apps → IT assigns groups |
| Governance | No access certification; no entitlement management; no SoD matrix |
| Monitoring | Default Entra log retention (30 days); no SIEM integration for identity events |
| Workload identity | 340 service principals, of which 2 Copilot agents and 4 Power Platform connections hold broad Graph application permissions from a 2025 pilot, never reviewed |

## Identity population

| Population | Count | Governance gap |
| --- | --- | --- |
| Employees | 2,000 | Leaver process manual and unmeasured |
| Contractors | 300 | No expiry date held on identity; no sponsor |
| Guests / B2B | 90 | No expiry, no review, no sponsor |
| Service & shared accounts | 145 | Static passwords, shared knowledge, no named owner |
| Workload identities (SPNs, managed identities) | 340 | No inventory, no owner, no permission review |

Non-human identities outnumber the IT department by roughly five to one and are governed by nothing. This
is the finding that surprised the Audit & Risk Committee most, and it is the one that maps most directly
to where the industry is heading — the same governance gap now appearing around AI agents.

## Baseline metrics captured at assessment

These form the "before" line in every subsequent measurement. Without them, no residual-risk claim later
in this portfolio is provable.

| Metric | Baseline |
| --- | --- |
| Permanent Global Administrators | 12 |
| Privileged assignments that are eligible rather than permanent | 0% |
| MFA enforced by policy (not per-user) | 0% |
| Users with any MFA method registered | 71% |
| Legacy authentication sign-ins per 30 days | 4,180 |
| Median time from termination date to account disable | 9 days |
| Terminated accounts still enabled at assessment | 34 |
| Contractor identities with an expiry date set | 0% |
| Critical applications under periodic certification | 0 of 4 |
| Groups with a recorded owner | 68% |
| Identity log retention | 30 days |
| Microsoft Identity Secure Score | 48% |

## Assessment against Microsoft Identity Secure Score

Secure Score is used as a corroborating signal, not as the assessment itself. A score is a vendor's
weighted opinion of your configuration; it does not know which of your applications releases payments.
The register drives priority, and Secure Score is checked afterwards to confirm the treatment plan moves
it — from a baseline of 48% to a modelled 79% on completion of Wave 2.

**Technical evidence:** Lab 10 — Monitoring, Logs & Identity Secure Score.
