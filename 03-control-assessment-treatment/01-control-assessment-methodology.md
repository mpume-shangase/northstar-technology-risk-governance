# Control Assessment Methodology

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**CRISC Domain 3 — Risk Response & Reporting (32%)**

---

## 1. Why this phase exists

Project 02 established what could go wrong and how badly. It deliberately stopped at inherent risk,
because residual risk asserted before controls are tested is an estimate wearing the costume of a
measurement.

This phase answers the question that determines every treatment decision: **do the controls Northstar
already has actually work?**

The answer materially changes the investment case. If existing controls work, the gap is small and
treatment is targeted. If they do not, the organisation has been paying for assurance it never received —
and the first tranche of treatment is making existing controls operate rather than buying new ones.

## 2. Design effectiveness vs operating effectiveness

These are assessed separately because they fail for different reasons and are fixed by different means.

| | Question | Typical failure | Typical remedy |
| --- | --- | --- | --- |
| **Design effectiveness** | If this control operated exactly as intended, would it reduce the risk? | Control addresses the wrong thing, has gaps in scope, or depends on an assumption that doesn't hold | Redesign — often cheap |
| **Operating effectiveness** | Is it actually operating, consistently, with evidence? | Control exists on paper, is applied inconsistently, or produces no evidence | Enforcement, automation, ownership — often the harder fix |

A control must pass **both** to be rated Effective. A well-designed control that nobody operates provides
exactly as much protection as no control, but generates far more false assurance — which is worse, because
management stops looking.

### Rating scale

| Rating | Meaning | Effect on residual likelihood |
| --- | --- | --- |
| Effective | Well designed, operating consistently, evidenced | Full reduction |
| Partially effective | Well designed, inconsistently applied or unevidenced | No reduction; noted as partial mitigation |
| Ineffective | Design gap, or designed well but not operating | No reduction |
| Absent | No control exists | No reduction |

## 3. Testing approach

| Control type | Test method | Sample |
| --- | --- | --- |
| Automated preventive | Configuration inspection plus negative testing — attempt the action the control should block | Full population where queryable |
| Automated detective | Verify alert fires on a seeded condition; confirm routing and response | 3 seeded events |
| Manual preventive | Walkthrough plus evidence inspection | 25 items, or full population if fewer |
| Manual detective | Evidence of performance for each required period | All periods in the last 12 months |
| Corrective | Test the recovery or remediation actually completes within the stated objective | 1 full end-to-end test |

**Negative testing matters more than inspection.** Confirming a Conditional Access policy exists is not a
test; attempting sign-in from a non-compliant device and observing the block is. Five controls at
Northstar passed inspection and failed negative testing — most notably C-05, where remediation SLAs were
correctly defined and never enforced.

## 4. Results

Twenty-five controls were assessed against the 24 risk scenarios.

| Overall rating | Count | Share |
| --- | :-: | :-: |
| Effective | **0** | 0% |
| Partially effective | 3 | 12% |
| Ineffective | 11 | 44% |
| Absent | 11 | 44% |

### The most useful split is design vs operation

| | Count | Interpretation |
| --- | :-: | --- |
| Design Effective but not operating | 4 | C-05, C-06, C-21, C-23. **These are the cheap wins.** The thinking is already done; they need enforcement, ownership and evidence, not redesign. |
| Design Ineffective | 9 | Require redesign before they can be operated. |
| Absent | 11 | Require building. |

Four controls were designed correctly and simply not run. Backup restoration (C-23) is the clearest
example: the procedure is sound, the schedule is defined, and it has not been performed since 2024. That
is a management failure, not an engineering one, and it costs nothing but attention to fix.

## 5. Treatment option selection

Each above-appetite scenario was assessed against all four responses before mitigation was assumed.
Defaulting to "mitigate" everywhere produces a plan that is technically sound and commercially
unapprovable.

| Option | Applied to | Rationale |
| --- | --- | --- |
| **Avoid** | None | No scenario could be removed by ceasing the underlying activity. Northstar cannot stop using suppliers, cloud or AI. |
| **Transfer** | Partial — CYB-01, CYB-02 | Cyber insurance covers financial loss. It transfers no regulatory, operational or reputational consequence, so it is treated as a financial backstop, not a control. |
| **Accept** | TPR-03 in full; CYB-02, TPR-01, TPR-02, EMT-03, RES-01 in part | Five formal acceptances — see [`05-risk-treatment-plan.md`](./05-risk-treatment-plan.md). |
| **Mitigate** | 23 of 24 | Primary response. |

**TPR-03 is the only pure acceptance.** Supplier concentration across ERP, identity and email cannot be
meaningfully reduced within the cycle — diversifying would cost more than the exposure and introduce
integration risk of its own. It is accepted with concentration measured, an exit plan documented, and
reporting to the Technology Risk Committee.

## 6. Residual scoring

Residual likelihood is reduced only by controls rated Effective **after** treatment. Impact is held
constant unless the treatment genuinely changes the consequence — which it rarely does.

That last point is the one most often got wrong. Enforcing MFA does not make a fraudulent payment less
expensive; it makes it less likely. Fifteen of 24 scenarios retain their original impact score after
treatment, and that is correct rather than a failure of ambition.

| | Inherent | Residual | Change |
| --- | :-: | :-: | :-: |
| Aggregate exposure | 330 | 169 | −49% |
| Above appetite (≥15) | 13 | **0** | −13 |
| Critical (20–25) | 3 | 0 | −3 |
| Low band (≤7) | 0 | 11 | +11 |
| Highest single scenario | 20 | 10 | −50% |

## 7. Limitations

- **Residual scores are forecast, not measured.** They represent the position once treatment completes.
  Each wave close re-tests the controls and re-scores; only then is residual observed rather than modelled.
- **Four controls could not be fully tested** because the systems in scope fall inside the asset inventory
  gap. Their ratings rest on walkthrough rather than evidence inspection.
- **No independent validation.** Testing was performed by second line. Internal Audit assurance over this
  assessment is scheduled for the following cycle.
