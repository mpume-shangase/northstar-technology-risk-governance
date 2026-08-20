# Key Risk Indicator Catalogue

> ⚠️ Constructed case study. See [`disclaimer.md`](./disclaimer.md).
>
> **Canonical source.** KRI IDs are stable across the programme. Projects 02, 03 and 04 report against
> these definitions rather than inventing their own.

## Definitions

KRIs are leading indicators of risk materialising. They are distinct from KPIs, which measure whether the
programme is delivering. Both are reported; only KRIs drive escalation.

| ID | KRI | Related risk | Green | Amber | Red | Source |
| --- | --- | --- | --- | --- | --- | --- |
| KRI-01 | Terminated accounts still enabled >24h after last working day | R-01 | 0 | 1–2 | ≥3 | Lifecycle Workflows report |
| KRI-02 | Permanent (non-eligible) privileged role assignments | R-02 | ≤2 | 3–5 | ≥6 | PIM assignment export |
| KRI-03 | Non-employee identities past expiry with active access | R-03 | 0 | 1–4 | ≥5 | Access package report |
| KRI-04 | Users holding entitlements from a previous role >30 days after transfer | R-04 | ≤5 | 6–15 | ≥16 | Access review output |
| KRI-05 | Tier 1 applications with an overdue certification cycle | R-05 | 0 | 1 | ≥2 | Access Reviews |
| KRI-06 | Active identities without policy-enforced MFA | R-06 | 0 | 1–10 | ≥11 | Conditional Access insights |
| KRI-07 | Legacy authentication sign-ins per 30 days | R-07 | 0 | 1–50 | ≥51 | Sign-in logs |
| KRI-08 | Workload identities holding high-privilege Graph permissions | R-08 | ≤11 | 12–15 | ≥16 | Graph enumeration |
| KRI-09 | Guest accounts dormant >90 days | R-09 | ≤5 | 6–20 | ≥21 | Guest access review |
| KRI-10 | Break-glass sign-ins not matched to a documented incident | R-10 | 0 | — | ≥1 | Log Analytics alert |
| KRI-11 | Service accounts with passwords unrotated >365 days | R-11 | 0 | 1–5 | ≥6 | Vault report |
| KRI-12 | Tier 1 sign-ins from non-compliant devices | R-12 | 0 | 1–20 | ≥21 | Conditional Access insights |
| KRI-13 | Unresolved SoD conflicts | R-13 | ≤23 | 24–28 | ≥29 | SoD conflict report |
| KRI-14 | Days of identity log retention available | R-14 | ≥365 | 90–364 | <90 | Log Analytics workspace |

## Operating notes

- KRI-10 has no amber band. A break-glass sign-in is either explained or it is an incident.
- KRI-08 and KRI-13 are set at the *treated* baseline, not at zero. Setting a threshold you are already
  breaching produces a permanently red dashboard, which trains executives to ignore the dashboard.
- Amber requires the control owner to act; red triggers the escalation path above.
- KRIs are reported monthly to the IAM Lead and CISO, quarterly to the Audit & Risk Committee.

**Technical evidence for KRI collection:** Lab 10 — Monitoring, Logs & Identity Secure Score.
