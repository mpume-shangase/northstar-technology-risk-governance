# Risk Scoring Model & Appetite Statement

> ⚠️ Constructed case study. See [`disclaimer.md`](./disclaimer.md).
>
> **Canonical source.** All four projects score risk using this model. Any scenario scored anywhere in
> this repository uses these bands and this appetite statement.

## Scoring model

Likelihood and impact are each scored 1–5. Inherent score = Likelihood × Impact.

## Likelihood

| Score | Definition | Frequency anchor |
| --- | --- | --- |
| 5 | Almost certain | Expected multiple times per year, or already occurring |
| 4 | Likely | Expected at least annually |
| 3 | Possible | Expected within 3 years |
| 2 | Unlikely | Expected within 10 years |
| 1 | Rare | Not expected; requires exceptional circumstances |

## Impact

Impact is business impact, not technical severity. A scenario scores on the highest applicable dimension.

| Score | Financial | Operational | Regulatory / reputational |
| --- | --- | --- | --- |
| 5 | > CAD 1M | Multi-site production halt > 24h | Reportable breach, regulator engagement, customer contract loss |
| 4 | CAD 250K–1M | Single-site disruption > 8h | Reportable breach, material audit finding |
| 3 | CAD 50K–250K | Departmental disruption | Internal audit finding, customer questionnaire failure |
| 2 | CAD 10K–50K | Minor, workaround available | Internal policy exception |
| 1 | < CAD 10K | Negligible | None |

## Risk bands and appetite

| Band | Score | Board-approved treatment posture |
| --- | --- | --- |
| Critical | 20–25 | Unacceptable. Treat immediately; escalate to CEO. |
| High | 15–19 | Above appetite. Treat within current fiscal year. |
| Moderate | 8–14 | Within appetite with active monitoring and named owner. |
| Low | 1–7 | Within appetite. Accept and review annually. |

**Risk appetite statement (as ratified by the Audit & Risk Committee):** *Northstar Global accepts no
identity risk scoring 15 or above. Moderate identity risk is accepted where a named control owner,
a monitoring KRI and a review date exist. The organisation has no appetite for standing privileged access
to financial systems, nor for undetected access retention after employment ends.*

The appetite statement matters more than the scoring model. It converts "this feels bad" into "this
breaches a decision the board already made," which is what actually releases budget.

