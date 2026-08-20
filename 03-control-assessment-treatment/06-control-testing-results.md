# Control Testing Results

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

Full library with framework mappings and owners:
[`02-control-library.csv`](./02-control-library.csv) · Method:
[`01-control-assessment-methodology.md`](./01-control-assessment-methodology.md)

---

## Summary

| Overall rating | Count | Share |
| --- | :-: | :-: |
| Effective | **0** | 0% |
| Partially effective | 3 | 12% |
| Ineffective | 11 | 44% |
| Absent | 11 | 44% |

Twenty-five controls tested. None passed both design and operating effectiveness.

## Design vs operation

| Design rating | Count | What it means for cost |
| --- | :-: | --- |
| Effective | 4 | **Cheapest tranche.** Thinking already done; needs enforcement and evidence, not redesign |
| Partially effective | 1 | Scope extension only |
| Ineffective | 9 | Redesign before operation |
| Absent | 11 | Build from nothing |

### The four cheap wins

| Control | Designed correctly | Not operating because |
| --- | --- | --- |
| C-05 Vulnerability remediation SLA | SLA defined, tooling in place, ownership clear | Nothing escalates when the SLA passes. 34 criticals overdue, oldest 118 days |
| C-06 EDR coverage | Correct product, correct policy | Deployment stopped at 82%; no coverage KPI reported |
| C-21 Change control | CAB functions well for major change | Standard changes never brought into scope; 11 unauthorised changes in a 90-day sample |
| C-23 Backup restore testing | Procedure sound, schedule defined | Not performed since 2024 |

These four are management failures rather than engineering ones. C-23 is the starkest: every resilience
claim in the register depends on restores working, and nobody has confirmed they do for over a year.

## Controls that passed inspection and failed negative testing

Inspection confirms a control exists. Negative testing confirms it does something. Five controls looked
correct on inspection and failed when tested against:

| Control | Inspection showed | Negative test |
| --- | --- | --- |
| C-05 | Remediation SLA documented and assigned | Vulnerabilities aged past SLA with no escalation, alert or exception |
| C-13 | Region restrictions configured | Resource created successfully in a non-approved region on 3 of 5 platforms |
| C-21 | Change process documented and CAB minuted | Change deployed outside process completed without detection |
| C-24 | Incident process references regulatory notification | Simulated reportable incident produced no notification trigger or timer |
| C-06 | EDR console shows healthy estate | Console reports only enrolled devices; the 18% gap is invisible from within the tool |

C-06 is worth dwelling on. The tool reported 100% healthy because it can only report on what is enrolled.
A control that measures its own coverage using itself will always look complete — this is the most common
way well-intentioned monitoring produces false assurance.

## By risk category

| Category | Controls | Effective | Absent | Weakest area |
| --- | :-: | :-: | :-: | --- |
| Cybersecurity | 8 | 0 | 3 | Identity controls absent entirely |
| Cloud & Infrastructure | 3 | 0 | 2 | No configuration baseline assessment |
| Data | 3 | 0 | 1 | Retention unenforceable without inventory |
| Third Party | 2 | 0 | 1 | No reassessment, no exit planning |
| Emerging Technology | 4 | 0 | 3 | No AI governance controls exist at all |
| Technology Operations | 2 | 0 | 0 | Both partially operating |
| Resilience | 2 | 0 | 0 | Designed but untested |
| Compliance & Regulatory | 2 | 0 | 1 | No evidence retention |

Emerging Technology has three of four controls absent — consistent with the Project 02 finding that
Northstar has been deploying AI for eighteen months and governing it for none.

## Root cause distribution

| Root cause | Issues | Implication |
| --- | :-: | --- |
| Control absent | 8 | Requires build and funding |
| Control design gap | 7 | Requires redesign; often cheaper than assumed |
| Control partially operating | 3 | Requires scope extension and coverage measurement |
| Control not operating | 2 | Requires ownership and enforcement only |

Twenty issues were raised. Four are Critical, eleven High, five Medium. Full log:
[`03-issues-and-findings-log.csv`](./03-issues-and-findings-log.csv).

## What testing could not establish

- **Four controls were assessed by walkthrough only**, because the systems in scope fall inside the 12–18%
  asset inventory gap. Their ratings rest on described process rather than inspected evidence.
- **No independent validation.** Testing was performed by second line; Internal Audit assurance over this
  assessment is scheduled for the following cycle.
- **Operating effectiveness for newly built controls cannot be tested until they have operated.** Wave 2
  and 3 controls carry forecast ratings that must be re-tested at wave close before residual risk is
  treated as measured rather than modelled.
