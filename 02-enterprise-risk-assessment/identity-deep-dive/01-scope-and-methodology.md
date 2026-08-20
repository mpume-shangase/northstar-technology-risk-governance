# 01 — Scope & Methodology

> ⚠️ Constructed case study. Northstar Global is fictional.

## 1. Assessment objective

Determine whether Northstar Global's identity estate carries risk exceeding the board-approved appetite,
and if so, define proportionate treatment. The assessment answers three questions the Audit & Risk
Committee asked directly:

1. Can an external attacker reach a finance-critical system using only credentials?
2. Do people and non-human identities retain access they no longer need?
3. If an identity-driven incident occurred, could we evidence what happened and who authorised the access?

## 2. Scope

**In scope**

- Entra ID tenant, all human identities (employee, contractor, guest)
- Workload identities: service principals, managed identities, app registrations, Copilot and Power
  Platform agents
- Authentication and authorisation controls: Conditional Access, MFA methods, password policy, PIM
- Joiner–Mover–Leaver process end to end, including the HR-to-IT handoff
- Entitlement review and certification practices for the four critical applications
- Privileged access to Entra, Azure subscriptions and on-prem AD

**Out of scope**

- Endpoint security, network segmentation, physical security
- Application-internal authorisation logic within SAP (assessed at the access-provisioning boundary only)
- OT network identity beyond the AD-integrated front end
- Data classification and DLP (referred to a parallel workstream)

Scope boundaries are stated because an assessment that claims to cover everything is either dishonest or
useless. The OT exclusion in particular is a known limitation and is flagged in the executive summary.

## 3. Method

| Phase | Activity | Output |
| --- | --- | --- |
| 1. Context | Business impact interviews with Finance, Operations, HR and IT leadership; documented risk appetite | Appetite statement, critical asset list |
| 2. Discovery | Tenant configuration review, Graph queries for sign-in and permission data, access-path walkthroughs, process interviews | Evidence pack |
| 3. Analysis | Scenario construction, likelihood and impact scoring, control effectiveness testing | Risk register (inherent) |
| 4. Gap assessment | Current-state maturity per control domain against target | Control-gap assessment |
| 5. Response | Treatment option selection, sequencing, costing, residual scoring | Risk-treatment plan |
| 6. Report | Executive summary, committee presentation, KRI baseline | Executive summary |

### Discovery evidence sources

Evidence was gathered rather than assumed. The following were the primary sources:

- Entra sign-in logs, filtered for legacy authentication client apps over a 90-day window
- `Get-MgServicePrincipal` and Graph enumeration of application and delegated permission grants
- Directory role assignment export, separating eligible from permanently active assignments
- Guest account export with `externalUserState`, creation date and last sign-in
- HR joiner/leaver ticket sample (n=60) measured against actual account disable timestamps
- Conditional Access policy export and gap analysis against the identity/device/application matrix

## 4. Scoring model

Likelihood and impact are each scored 1–5; inherent score = Likelihood × Impact. The full scale
definitions, risk bands and the board-approved appetite statement are held once for the whole programme in
[`../00-programme/risk-scoring-model.md`](../../00-programme/risk-scoring-model.md).

The threshold that matters throughout this assessment: **Northstar accepts no identity risk scoring 15 or
above.**

## 5. Control effectiveness rating

Existing controls were not assumed effective because they existed. Each was rated:

| Rating | Meaning |
| --- | --- |
| Effective | Designed correctly, operating consistently, evidenced |
| Partially effective | Designed correctly but inconsistently applied or unevidenced |
| Ineffective | Design gap, or not operating |
| Absent | No control in place |

Only *Effective* controls reduce the likelihood score. *Partially effective* controls were treated as
absent for scoring purposes and noted separately — a Conditional Access policy in report-only mode is
documentation, not a control.

## 6. Limitations

- Assessment is point-in-time (Q1 modelled) and does not account for configuration drift after fieldwork.
- Likelihood scoring uses industry incident-frequency benchmarks, not Northstar-specific historical data,
  because incident records prior to the current SIEM deployment are incomplete.
- Impact estimates for production disruption were provided by Operations and not independently validated.
- OT identity exclusion means the assessment cannot speak to a plausible IT-to-OT lateral path.
