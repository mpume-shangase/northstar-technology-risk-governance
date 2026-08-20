# Business Impact Analysis — Methodology

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**CRISC Domains 1, 2 and 4** — Governance · Risk Assessment · Technology & Security

---

## 1. Why this assessment exists

[Project 02](../02-enterprise-risk-assessment/) scored RES-01 at 15 — recovery may exceed the maximum
tolerable disruption for customer order processing. [Project 03](../03-control-assessment-treatment/)
rated the supporting controls Ineffective: RTO documented for 4 of 9 critical services, end-to-end
recovery never tested, and backup restoration not performed since 2024. The residual position was
formally accepted at 10 under **ACC-05**.

That acceptance was made on an estimate. This assessment replaces the estimate with a measurement, and
tests whether the accepted position is actually the position.

## 2. The three questions a BIA answers

| Question | Metric | Set by |
| --- | --- | --- |
| How long can the business survive without this? | **MTD** — Maximum Tolerable Disruption | The business, never IT |
| How quickly must technology restore it? | **RTO** — Recovery Time Objective | Derived from MTD, minus workaround capacity |
| How much data can we afford to lose? | **RPO** — Recovery Point Objective | The business, based on reconstruction cost |

**MTD is a business judgement and RTO is a technology commitment.** Conflating them is the most common BIA
failure: IT states an RTO based on what the platform can currently do, the business accepts it because it
sounds authoritative, and nobody ever establishes what the business actually needed. The gap then stays
invisible until an incident makes it obvious.

At Northstar this is precisely what had happened. Four services carried a documented RTO. All four had
been set by IT from platform capability. None had been derived from a business MTD.

## 3. Impact over time, not impact at a point

A single impact figure is misleading because disruption cost is non-linear. Order processing at four hours
is recoverable through manual capture; at seventy-two hours the orders have gone to a competitor.

Impact was therefore assessed at three horizons — 4h, 24h and 72h — across four dimensions:

| Dimension | Basis |
| --- | --- |
| Financial | Lost or delayed revenue, penalties, recovery cost |
| Operational | Production, dispatch, service delivery capacity |
| Regulatory | Statutory deadlines, traceability obligations, reporting |
| Reputational | Customer-visible failure, contractual assurance commitments |

**Aggregate exposure: CAD 325,000 at 4 hours · CAD 2.27M at 24 hours · CAD 7.81M at 72 hours.**

The shape of that curve is the argument for investment. Northstar's current recovery capability sits
almost entirely in the steep part of it.

## 4. Manual workaround capacity

Every process was assessed for what actually happens when technology is unavailable. Workarounds extend
MTD — but only for as long as they hold, and each accumulates a debt that must be repaid afterwards.

| Process | Workaround | Holds for | Debt created |
| --- | --- | --- | --- |
| BP-01 Order capture | Phone and email to spreadsheet | 25% of volume | Re-keying, error correction, missed SLAs |
| BP-02 Production scheduling | Printed schedule from last known good | 40% for 48h, then nothing | Material misallocation |
| BP-03 Quality release | Paper batch records | 60% | Reconciliation debt against traceability obligations |
| BP-06 Payroll | Repeat prior period payment | One cycle only | Corrections, variance queries, potential underpayment |

**Workarounds that hold at 60% capacity are not continuity, they are managed degradation.** Quality release
is the sharpest case: paper batch records keep dispatch moving while creating a reconciliation obligation
against product traceability requirements that grows every hour.

## 5. Deriving RTO from MTD

`Required RTO = tightest MTD of any dependent process − workaround capacity − recovery verification time`

Applied to nine critical services. The dependency direction matters: a service inherits the tightest MTD
of anything that depends on it. SAP supports payment release (MTD 24h) but also order management (MTD 4h),
so its required RTO derives from 4h, not 24h.

**Six of nine services cannot recover within the time the business can tolerate.** Three have significant
gaps of 16 hours or more.

## 6. Single points of failure

Three services have no alternative path:

| Service | Why | Consequence |
| --- | --- | --- |
| **SVC-01 Entra ID** | No alternative authentication route exists | Identity failure removes access to every other service simultaneously. Its 2-hour required RTO is the tightest in the estate, and its 4-hour current RTO is a vendor commitment Northstar cannot improve — only design around. |
| **SVC-04 Plant MES** | Single-site instance, no standby | Production scheduling stops at both major plants |
| **SVC-05 OT historian** | Single instance | Compounds SVC-04 |

SVC-01 deserves particular attention because it inverts the usual assumption. Northstar cannot make Entra
recover faster; it can only reduce what breaks when Entra is unavailable — cached credentials, break-glass
paths, offline procedures for the highest-MTD processes.

## 7. Validation

BIA figures are only as good as their source, and business owners systematically over-state criticality
when asked directly. Three techniques were used to counter this:

- **Impact figures were derived from records** — order values, production rates, penalty clauses — not
  from owner estimates alone.
- **MTD was tested against history.** Where a process had previously experienced disruption, actual
  behaviour was compared with the claimed tolerance. Two processes had claimed MTDs shorter than
  disruptions they had already survived without material consequence.
- **Owners were asked to justify why the workaround could not extend further**, rather than asked how
  quickly they needed recovery. The second question always returns "immediately".

BP-05 and BP-07 were revised upward as a result. That correction matters commercially — an
over-stated MTD produces over-investment in the wrong service, which is a real cost with no risk benefit.

## 8. Limitations

- Impact estimates for production disruption were provided by Operations and validated against production
  records, but not independently audited.
- Vendor RTOs are contractual commitments, not tested capability. Northstar has never observed SVC-01,
  SVC-06, SVC-07, SVC-08 or SVC-09 actually recover.
- The OT process control network beyond the historian front end remains out of scope, consistent with the
  enterprise assessment boundary. A plant-floor scenario is therefore assessed only to the IT boundary.
