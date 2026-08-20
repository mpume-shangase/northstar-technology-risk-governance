# Resilience Improvement Plan

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

Addresses six services with recovery gaps and ten tabletop findings.

---

## Sequencing logic

Ordered by **exposure closed per dollar**, with one override: anything that removes a circular dependency
comes first regardless of cost, because a circular dependency invalidates the recovery plan itself rather
than merely slowing it.

| Wave | Theme | Weeks | Addresses | Cost (CAD) |
| --- | --- | --- | --- | --- |
| 1 | Make the plan executable | 1–8 | F-01 to F-05, F-07, F-09 | 34,000 |
| 2 | Close the identity and data gaps | 9–20 | SVC-01, SVC-02, SVC-03, SVC-06 | 186,000 |
| 3 | Close the plant gaps | 21–40 | SVC-04, SVC-05 | 295,000 |
| | **Total** | **40 weeks** | | **515,000** |

## Wave 1 — Make the plan executable (weeks 1–8)

**Rationale:** seven of the ten tabletop findings cost almost nothing to fix and every one of them would
have extended a real outage. This wave buys no technology.

| # | Action | Finding | Owner |
| --- | --- | --- | --- |
| 1.1 | Assign and publish single-point authority for production halt, with named deputy | F-01 | COO |
| 1.2 | Establish out-of-band incident communications independent of Entra and M365; printed contact list held at both plants and by each incident role | F-02 | CISO |
| 1.3 | Document and test Active Directory forest recovery procedure | F-03 | Head of IT Operations |
| 1.4 | Verify backup immutability and isolation from the production domain; perform full restore test per critical service | F-04 | Head of IT Operations |
| 1.5 | Embed regulatory notification triggers and statutory timers in the incident workflow | F-05, ISS-18 | CCO |
| 1.6 | Define estate recovery sequencing by dependency, with Entra ID first | F-07 | CIO |
| 1.7 | Mandatory decision log during incidents, with a named scribe role | F-09 | CISO |
| 1.8 | Add escalation trigger when any process passes its MTD | F-10 | COO |

**Exit criteria:** production-halt authority published · out-of-band channel tested · AD recovery
documented and tested · restore verified for all 9 services · recovery sequence defined · re-run tabletop
and close F-01 to F-05.

**This wave costs CAD 34,000 — 7% of the programme — and addresses every Critical tabletop finding.**

## Wave 2 — Close the identity and data gaps (weeks 9–20)

| # | Action | Service | Gap closed |
| --- | --- | --- | --- |
| 2.1 | Design around the Entra RTO rather than attempting to improve it: cached credential policy, break-glass access, offline procedures for BP-01 and BP-02 | SVC-01 | 2h → tolerable |
| 2.2 | Warm standby for the order processing platform with tested failover | SVC-02 | 4h gap → 0 |
| 2.3 | SAP recovery uplift: full application-tier recovery, not database only; documented and tested end to end | SVC-03 | 8h gap → 0 |
| 2.4 | Quality system recovery procedure with vendor-supported restore path and tested export | SVC-06 | 16h gap → 4h |

**Note on 2.1.** SVC-01 is the only gap Northstar cannot engineer away — the 4-hour RTO is a vendor
commitment. The treatment is not to make identity recover faster but to reduce what breaks while it is
unavailable. This is the single most important design decision in the plan, and it is easy to miss because
the instinct is to attack the number rather than the dependency.

## Wave 3 — Close the plant gaps (weeks 21–40)

| # | Action | Service | Gap closed |
| --- | --- | --- | --- |
| 3.1 | Plant MES standby instance at second site with tested failover | SVC-04 | 20h gap → 2h |
| 3.2 | OT historian redundancy and documented recovery | SVC-05 | 18h gap → 4h |
| 3.3 | IT/OT segmentation at both major plants | ISS-09, F-06 | Removes lateral path |

3.3 is the CAD 340,000 capital item deferred under **ACC-02**. It is included here because this assessment
materially strengthens the case: the tabletop confirmed no participant could evidence containment, and the
BIA quantifies plant disruption at CAD 620,000 at 24 hours and CAD 2.1M at 72 hours.

## Costs against exposure

| Horizon | Aggregate business impact |
| --- | --- |
| 4 hours | CAD 325,000 |
| 24 hours | CAD 2,265,000 |
| 72 hours | CAD 7,810,000 |

Total programme cost of CAD 515,000 is less than a quarter of a single 24-hour estate outage, and 7% of a
72-hour one. Northstar's current capability places it firmly in the steep part of that curve: six services
cannot recover within business tolerance, and eight of nine have never been tested at all.

**Wave 1 alone — CAD 34,000 — addresses every Critical tabletop finding**, none of which requires
technology purchase. That is the number to put in front of the Committee first.

## Recommended revision to ACC-05

Acceptance ACC-05 records residual 10 for RES-01, expiring in 6 months. This assessment does not
recommend withdrawing it, but does recommend two amendments:

1. **Add a condition:** the acceptance holds only while Wave 1 completes to schedule. Its compensating
   controls were assumed, and the tabletop showed three of them were untested.
2. **Add a KRI:** count of critical services with an untested recovery procedure. Currently 8 of 9.
   Threshold red at 3 or more. Without this the acceptance has no monitoring, which the appetite statement
   requires for any Moderate retention.

## Ongoing assurance

| Activity | Frequency | Owner |
| --- | --- | --- |
| Backup restore test per critical service | Quarterly | Head of IT Operations |
| End-to-end recovery test, rotating service | Semi-annual | Head of IT Operations |
| Tabletop exercise, alternating scenario type | Semi-annual | CISO |
| BIA refresh | Annual, or on material business change | COO |
| RTO/RPO reconfirmation against MTD | Annual | Technology Risk |

The BIA refresh matters more than it appears. MTDs move when the business moves — a new distribution
contract with tighter delivery commitments shortens BP-01's tolerance, and every derived RTO shifts with
it. A BIA that is never refreshed becomes a record of what used to be tolerable.
