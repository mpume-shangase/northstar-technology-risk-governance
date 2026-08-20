# Risk Appetite & Tolerance Statement

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**Approved by:** Board of Directors · **Owned by:** Chief Risk Officer · **Review:** Annual
**Status:** Ratified

---

## Why appetite and tolerance are different

These terms are used interchangeably in most organisations and in a fair number of textbooks. The
distinction matters operationally:

| | Definition | Expressed as | Set by |
| --- | --- | --- | --- |
| **Appetite** | The amount and type of technology risk Northstar is *willing to pursue or retain* in pursuit of its objectives | Qualitative statements plus a numeric threshold | Board |
| **Tolerance** | The acceptable *variation* around appetite for a specific measure before action is required | Numeric thresholds per metric — green/amber/red | Technology Risk Committee, within Board appetite |

Appetite answers "would we accept this?" Tolerance answers "have we drifted, and by how much?"
A risk can sit within appetite while a tolerance threshold is breached — that combination is the early
warning the whole framework exists to produce.

---

## Board appetite statement

> Northstar Global accepts technology risk where it is necessary to serve customers, operate efficiently
> and compete. We do not accept technology risk that threatens the safety of our people, the continuity of
> customer supply, the confidentiality of personal data entrusted to us, or our licence to operate.
>
> We will not trade regulatory compliance for speed. We will accept short-term operational disruption in
> preference to unmanaged security exposure. We accept that innovation — including artificial
> intelligence — carries uncertainty, and we require that uncertainty be identified, owned and bounded
> before deployment rather than discovered afterwards.
>
> **No technology risk scoring 15 or above on the enterprise scale may be retained without a formal,
> time-boxed acceptance approved at the appropriate level.**

## Appetite by risk category

Appetite is not uniform. Stating a single organisational appetite is the most common way appetite
statements become useless — it forces the same threshold onto ransomware and onto a print server.

| Category | Appetite | Statement |
| --- | --- | --- |
| **Cybersecurity** | **Averse** | We do not accept known, exploitable exposure on internet-facing systems or on systems processing personal or payment data. Compensating controls do not substitute for remediation beyond agreed windows. |
| **Data — privacy & sovereignty** | **Averse** | Zero appetite for processing personal data without lawful basis, or for storing regulated data outside approved jurisdictions. |
| **Resilience — customer-facing** | **Minimal** | Disruption to customer order processing beyond the agreed maximum tolerable period is not accepted. Internal service disruption is accepted where recovery is demonstrable. |
| **Third party** | **Cautious** | Accepted where due diligence is complete, contractual controls exist and an exit path is documented. Concentration in a single provider for two or more critical services requires Committee approval. |
| **Emerging technology / AI** | **Open, bounded** | We actively pursue AI capability and accept the uncertainty that carries — provided each system has a named owner, a defined authority boundary, human review of consequential decisions, and monitoring. Autonomous action against production financial systems is not accepted. |
| **Technology operations** | **Cautious** | Change-related disruption accepted within defined windows with rollback. Unauthorised change is not accepted. |
| **Compliance & regulatory** | **Averse** | Zero appetite for known non-compliance with statutory obligations. |

Two of these deserve comment.

**Emerging technology is "open, bounded" rather than averse.** An organisation that declares zero appetite
for AI risk while deploying AI has written a statement its own staff will route around. The honest
position is that Northstar wants the capability, accepts the uncertainty, and constrains it with four
specific conditions — each of which is testable, and each of which becomes a control in Domain 3.

**Resilience is split by customer impact.** A single resilience appetite would either over-protect
internal tooling or under-protect order processing.

---

## Tolerance thresholds

Tolerances are the operational teeth. Each has a metric, thresholds, a data source, an owner and a defined
consequence on breach. A tolerance without a defined consequence is a dashboard decoration.

| # | Metric | Green | Amber | Red | Owner | Consequence on red |
| --- | --- | --- | --- | --- | --- | --- |
| T-01 | Risks above appetite (≥15) without formal acceptance | 0 | 1–2 | ≥3 | CRO | Escalate to Audit & Risk Committee at next sitting |
| T-02 | Overdue risk treatment actions on above-appetite risks | 0 | 1–3 | ≥4 | Risk owners | Executive Committee reviews resourcing |
| T-03 | Critical/high vulnerabilities on internet-facing assets past SLA | 0 | 1–5 | ≥6 | CISO | Change freeze on affected estate |
| T-04 | Customer order processing unavailability, rolling 90 days | ≤2h | 2–4h | >4h | COO | Resilience improvement plan mandated |
| T-05 | Critical suppliers without current due diligence | 0 | 1–2 | ≥3 | Procurement Director | New engagements with that supplier suspended |
| T-06 | AI systems in production without named owner and authority boundary | 0 | 1–2 | ≥3 | CIO | Deployment pause pending registration |
| T-07 | Unauthorised changes detected, rolling 30 days | 0 | 1–3 | ≥4 | Head of IT Ops | Change process review, CAB reinforcement |
| T-08 | Regulatory notifications missed or late | 0 | — | ≥1 | Chief Compliance Officer | Immediate Board notification |
| T-09 | Technology assets not in inventory (estimated coverage gap) | ≤5% | 6–15% | >15% | CIO | Discovery programme funded |
| T-10 | Formal risk acceptances past expiry | 0 | 1–2 | ≥3 | CRO | Acceptance lapses; risk reverts to untreated |

T-08 has no amber band — a missed regulatory notification is binary. T-09 exists because the framework's
stated dependency is an accurate asset inventory; a dependency that isn't measured is an assumption.

---

## Escalation thresholds

| Residual score | Band | Retention authority | Max acceptance | Reporting |
| --- | --- | --- | --- | --- |
| 20–25 | Critical | Board, on ARC recommendation | Time-boxed only, during active treatment | Board, immediately |
| 15–19 | High | Chief Risk Officer, ARC noted | 3 months | ARC quarterly |
| 8–14 | Moderate | Risk owner (executive) | 6 months | TRC monthly |
| 1–7 | Low | Control owner | 12 months | Annual review |

**Critical risk cannot be a resting state.** It may be carried while funded treatment is in flight, with
an end date. Any other treatment of Critical risk makes the appetite statement decorative — which is the
condition most appetite statements are actually in.

### Escalation triggers independent of score

Certain events escalate regardless of calculated score, because waiting for the assessment cycle would be
absurd:

- Any confirmed breach of personal data
- Any AI system found acting outside its documented authority boundary
- Any critical supplier entering insolvency, acquisition or announced service withdrawal
- Any single incident causing customer order processing loss beyond the tolerable window
- Any control failure that was previously reported as effective
- Any risk acceptance reaching expiry without a renewal decision

---

## How appetite is used

An appetite statement earns its place only if something is refused because of it. In practice it is
applied at four decision points:

1. **Investment approval** — proposals creating exposure above appetite require treatment funding in the
   same business case, not a follow-on one.
2. **Change and deployment** — deployments breaching a tolerance threshold are held.
3. **Risk acceptance** — the bands above determine who may accept, and for how long.
4. **Supplier onboarding** — a vendor whose assessed residual risk exceeds appetite is rejected or
   approved with binding conditions.

## Review

Reviewed annually by the Board, and out of cycle on: material change to the business or regulatory
environment, a major incident, acquisition or divestment, or three consecutive quarters of a red tolerance
that treatment has failed to clear — the last of which usually means the appetite was set at a level the
organisation was never resourced to hold.
