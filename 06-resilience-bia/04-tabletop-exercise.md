# Tabletop Exercise — Ransomware in the Plant-Adjacent Estate

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**Exercise date modelled:** Week 6 · **Duration:** 3 hours · **Format:** Facilitated discussion-based
**Scenario basis:** CYB-02 from the [enterprise risk register](../02-enterprise-risk-assessment/), which
carries residual 10 under acceptance **ACC-02**

---

## Objectives

1. Test whether documented recovery procedures survive contact with a realistic scenario
2. Establish whether decision authority is clear under time pressure
3. Validate the RTO assumptions in the [critical service map](./03-critical-service-map.csv)
4. Identify dependencies not visible in the BIA

**This exercise was designed to fail.** An exercise everyone passes has tested nothing. Injects were built
specifically to attack the assumptions the resilience position rests on.

## Participants

| Role | Function | Attended |
| --- | --- | --- |
| CISO | Incident command | Yes |
| CIO | Technology recovery | Yes |
| COO | Business continuity decisions | Yes |
| Head of IT Operations | Recovery execution | Yes |
| Head of Security Operations | Containment | Yes |
| Head of Operations | Plant impact | Yes |
| Chief Compliance Officer | Regulatory notification | Yes |
| Head of Customer Service | Customer communication | Yes |
| CFO | Financial authority | **Declined — represented by delegate** |
| Vendor Manager | Supplier coordination | **Not invited — omission noted as F-08** |

## Scenario

**T+0, Tuesday 04:20.** EDR alerts on suspicious encryption activity across twelve file servers in the
corporate estate. Two are in the plant-adjacent network segment. The quality management system is
unavailable. Plant MES is responding but slowly.

### Injects

| Inject | Time | Content | Intent |
| --- | --- | --- | --- |
| **I-1** | T+0:20 | Encryption confirmed spreading. Containment requires isolating the plant-adjacent segment, halting production at the two largest sites. | Force a production-halt decision under uncertainty |
| **I-2** | T+1:10 | Domain controllers are affected. Authentication is degrading. | Test the SVC-01 single point of failure |
| **I-3** | T+2:00 | Microsoft 365 is unaffected but staff cannot authenticate to reach it. | Test whether the communications plan survives its own dependency |
| **I-4** | T+3:30 | Backups exist. The most recent verified restore test is from 2024. | Test the ISS-02 finding under pressure |
| **I-5** | T+6:00 | A customer asks whether their data is affected. Legal asks whether this is reportable. | Test the regulatory clock and notification decision |
| **I-6** | T+18:00 | Recovery is progressing. Production has been down 14 hours against an 8-hour MTD. | Test escalation and business decision-making beyond tolerance |

---

## Findings

| ID | Finding | Severity | Inject | Owner |
| --- | --- | --- | --- | --- |
| **F-01** | No single role held authority to halt production. The COO and Head of Operations each believed the other held it. 22 minutes of exercise time elapsed before the decision was taken. | Critical | I-1 | COO |
| **F-02** | The communications plan depends on Microsoft 365, which depends on Entra ID. With authentication degraded, no participant could describe how the incident team would communicate. | Critical | I-3 | CISO |
| **F-03** | Active Directory forest recovery is undocumented. No participant could state the procedure or who would perform it. | Critical | I-2 | Head of IT Operations |
| **F-04** | Backup restore capability could not be confirmed. Participants could not state whether backups were immutable or reachable from the compromised domain. | High | I-4 | Head of IT Operations |
| **F-05** | Regulatory notification decision stalled. No participant could state when the statutory clock started or who decides reportability. Consistent with ISS-18. | High | I-5 | CCO |
| **F-06** | IT to OT lateral movement was assumed contained but no participant could evidence the segmentation. Confirms ISS-09 and the basis of acceptance ACC-02. | High | I-1 | Head of Infrastructure |
| **F-07** | Recovery sequencing was not defined. Participants defaulted to restoring the loudest system rather than the one others depend on. Entra ID was not identified as first. | High | I-2 | CIO |
| **F-08** | No supplier coordination role was present. Three of nine critical services are vendor-hosted and nobody was accountable for vendor engagement during recovery. | Medium | — | Vendor Manager |
| **F-09** | Decision log was not maintained during the exercise. Post-incident reconstruction and regulatory defensibility would both be compromised. | Medium | All | CISO |
| **F-10** | Production remained down 14 hours against an 8-hour MTD with no defined escalation trigger. Nobody raised that tolerance had been breached. | Medium | I-6 | COO |

## The three findings that matter most

**F-02 is the one that should concern the Committee.** The incident communications plan depends on the
service that the scenario disables. This is a circular dependency that no document review would surface —
it only appears when someone asks "how are we talking to each other right now?" It is also cheap to fix:
an out-of-band channel and a printed contact list.

**F-01 is not a technology problem.** Both executives were competent and available. Neither knew the
decision was theirs. Twenty-two minutes of ambiguity in an exercise becomes considerably longer under real
pressure, and every minute of it was production time inside an 8-hour tolerance.

**F-07 exposes an assumption the whole BIA rests on.** RTOs were assessed per service. Under pressure,
participants restored in order of visibility rather than dependency, which would have produced a longer
aggregate outage than any individual RTO suggests. **Service-level RTOs do not aggregate to an estate
recovery time unless sequencing is defined.**

## What the exercise says about ACC-05

Acceptance ACC-05 records residual risk of 10 for RES-01, on the basis that RTO definition and annual
testing reduce likelihood while impact remains 5.

The exercise does not invalidate that residual — but it establishes that three of the assumptions
underneath it were untested: that AD could be recovered, that backups were usable, and that recovery would
be sequenced sensibly. **The acceptance was sound as a decision and optimistic as an estimate.**

That distinction is worth stating to the Committee plainly. The response is not to withdraw the
acceptance; it is to close F-01 to F-04 before it expires, and to re-test.

## Exercise governance

- Exercises are held **semi-annually**, alternating a cyber scenario with a platform or vendor failure
  scenario.
- Findings enter the [issues log](../03-control-assessment-treatment/03-issues-and-findings-log.csv) with
  owners and dates, and are tracked to closure like any other finding rather than filed as exercise output.
- The next exercise **re-tests closed findings first**. An exercise that never revisits prior findings
  measures enthusiasm rather than improvement.
- The CFO's non-attendance is itself recorded. Financial authority under incident conditions was never
  tested, and delegate attendance is not equivalent when the question is who can commit spend at 04:20.
