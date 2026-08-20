# AI Risk Assessment Methodology

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**CRISC — spans all four domains** · Governance · Risk Assessment · Risk Response · Technology & Security
**Frameworks:** NIST AI RMF 1.0 · ISO/IEC 42001:2023 · EU AI Act risk classification

---

## 1. Why AI needs its own assessment

The enterprise assessment in [Project 02](../02-enterprise-risk-assessment/) identified four AI scenarios
carrying 67 points — the highest exposure per scenario of any category. This assessment found **sixteen**,
and six of them were invisible to a conventional technology risk method: bias, prompt injection, model
drift, oversharing amplification, agent chaining, and silent model failure.

That gap is the argument for a dedicated method. Standard technology risk assessment asks whether a system
is available, confidential and has integrity. AI systems fail differently.

| Conventional system | AI system |
| --- | --- |
| Fails visibly — it stops working | Fails silently — it keeps producing plausible output that is wrong |
| Behaviour is deterministic and testable | Behaviour is probabilistic; the same input may not produce the same output |
| Access is what the user has | Access is what the *agent* has, acting on behalf of a user who may not know what it can reach |
| Input is data | Input may contain instructions — untrusted content becomes an attack surface |
| Correct today stays correct | Correct today drifts as the world changes underneath the model |
| One system, one assessment | Agents invoke agents; the combined privilege path was never assessed |

**Silent failure is the defining property.** A database that goes down announces itself. A forecasting
model that quietly degrades produces confident numbers that inform inventory decisions for months.

## 2. Autonomy tiering

Governance requirement is driven by **autonomy × data sensitivity**, not by whether something is labelled
"AI". A chatbot that only suggests text needs less control than a flow that posts to the ledger, even
though both use the same model.

| Tier | Definition | Human involvement | Minimum controls |
| --- | --- | --- | --- |
| **A0 Assistive** | Suggests; a human decides and acts | Human acts on every output | Data handling · usage guidance |
| **A1 Supervised** | Acts, but each action requires human approval | Approval per action | A0 plus action logging · scoped permissions |
| **A2 Delegated** | Acts within defined bounds; human reviews after the fact | Post-hoc review, sampled | A1 plus documented authority boundary · drift monitoring · full logging |
| **A3 Autonomous** | Acts without review inside its remit | Exception-based only | A2 plus pre-deployment assurance · kill switch · Committee approval per system |

Northstar operates no A3 systems today. Four sit at A2, and **none of the four has a documented authority
boundary** — meaning their bounds exist only in the intent of whoever built them.

## 3. The authority boundary

The single most useful artefact in AI governance, and the one almost nobody produces. For each system it
states, in writing:

- **What it may do** — the specific actions available to it
- **What it may reach** — data, systems, and the identity it acts as
- **What it may never do** — explicit prohibitions, not implied ones
- **Who it acts on behalf of** — and whether that principal's permissions bound it
- **What happens at the boundary** — refuse, escalate, or halt
- **Who owns it** — a named individual, not a team

**A boundary that exists only in a prompt is not a control.** Prompts are advisory to the model and can be
overridden by the model's own reasoning or by injected content. The boundary must be enforced where the
permissions are — in the identity, the API scope, the connector configuration — with the prompt as
reinforcement rather than mechanism.

This is the difference between "we told it not to" and "it cannot".

## 4. Discovery

Inventory cannot rely on records of what was approved, because the highest-risk systems are the ones
nobody approved. Four methods were used:

| Method | Found |
| --- | --- |
| IT and procurement records | 11 sanctioned systems |
| Network telemetry — traffic to known AI service endpoints | 2 shadow systems |
| Platform enumeration — Power Platform and Copilot Studio environments | 1 system absent from IT records |
| Vendor product review — AI embedded in existing SaaS | 2 systems nobody classified as AI |

The last row matters disproportionately. **Embedded vendor AI is the most under-governed category**,
because it arrives inside a product that was assessed before the AI existed and never reassessed. Nobody
procures "an AI system"; they procure a CRM that later ships AI features.

## 5. Risk categories assessed

Sixteen scenarios across nine categories, mapped to NIST AI RMF functions:

| Category | Scenarios | Not visible to conventional assessment |
| --- | :-: | :-: |
| Data leakage | AI-01 | |
| Bias and fairness | AI-02 | ✓ |
| Excessive privilege | AI-03 | |
| Authority and autonomy | AI-04 | |
| Output reliability | AI-05, AI-13 | ✓ |
| Prompt injection | AI-06 | ✓ |
| Vendor model training | AI-07 | |
| Ownership and lifecycle | AI-08 | |
| Model drift | AI-09 | ✓ |
| Oversharing amplification | AI-10 | ✓ |
| Auditability | AI-11 | |
| Regulatory | AI-12 | |
| Privacy | AI-14 | |
| Agent chaining | AI-15 | ✓ |
| Cost | AI-16 | |

## 6. Regulatory classification

Each system is classified against EU AI Act risk tiers, since Northstar operates in Poland and processes
data on EU-resident applicants.

**AI-SYS-11, the CV screening tool, is high-risk.** Employment and worker selection is explicitly listed.
That classification brings obligations on transparency, human oversight, record-keeping, accuracy and
conformity — none of which Northstar currently meets, and none of which anyone had considered, because the
tool was procured as recruitment software rather than as an AI system.

It is also the only system at A2 Delegated autonomy with maximum data sensitivity and **no human review of
rejections**. A candidate rejected by that system today cannot be given a reason, because no explanation is
recorded.

## 7. Scoring

Likelihood and impact are scored 1–5 using the enterprise model in
[`../00-programme/risk-scoring-model.md`](../00-programme/risk-scoring-model.md), so AI risk aggregates
with the enterprise register rather than sitting in a parallel universe of its own. That consistency is
deliberate: a separate AI scoring scale would make AI exposure incomparable with everything else, and the
Committee would have no way to judge whether it deserves the investment.

| | Inherent | Residual | Change |
| --- | :-: | :-: | :-: |
| Aggregate exposure | 218 | 92 | −58% |
| Above appetite (≥15) | 7 | 0 | −7 |
| Critical (20–25) | 3 | 0 | −3 |

## 8. Limitations

- **Likelihood calibration is weak.** The technology is too new for reliable base rates. Scores rest on
  observed internal conditions — traffic seen, permissions enumerated, boundaries absent — rather than
  external frequency data. Where a scenario had no observable internal evidence, it was scored
  conservatively and flagged.
- **Shadow AI discovery is a floor, not a ceiling.** Telemetry finds traffic to *known* AI endpoints.
  Services not on the list, or reached through personal devices, remain invisible.
- **Bias in AI-SYS-11 was not independently tested.** The finding rests on the absence of vendor testing
  evidence, not on measured disparate outcomes. Northstar cannot currently test it, because no decision
  records are retained.
