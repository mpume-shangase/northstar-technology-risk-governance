# Board Technology Risk Report — Q2

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**To:** Board of Directors · **From:** Chief Risk Officer, on recommendation of the Audit & Risk Committee
**Period:** Q2 · **Classification:** Board Confidential

---

## Position against appetite

**Board appetite: no technology risk scoring 15 or above may be retained without formal, time-boxed
acceptance.**

| | Q1 baseline | Q2 actual | Q2 plan | Q4 target |
| --- | :-: | :-: | :-: | :-: |
| Aggregate exposure | 330 | **271** | 259 | 169 |
| Scenarios above appetite | 13 | **9** | 8 | 0 |
| Critical scenarios (20–25) | 3 | **0** | 0 | 0 |
| Formal acceptances in force | 0 | 5 | 5 | 5 |

![Aggregate exposure trend and forecast](./assets/exposure-trend.svg)

**Exposure is down 18% since baseline. It is 4.6% behind plan.** All three Critical scenarios have been
cleared. Nine scenarios remain above appetite, each under active treatment with a named owner and a date.

## Why we are behind plan

Two Wave 1 actions slipped, both for the same reason: they depend on completing the technology asset
inventory, which is at 86% coverage against a 95% target.

| Action | Owner | Original | Revised | Effect |
| --- | --- | --- | --- | --- |
| Complete EDR deployment to all endpoints | CISO | Week 10 | Week 16 | 41 endpoints uncovered; CYB-02 unchanged |
| Remediate end-of-life systems | CIO | Week 20 | Week 26 | 14 systems; OPS-02 unchanged |

Neither slip creates new exposure. Both delay reduction already committed. The dependency is the same in
each case, which is why the recommendation below concerns inventory rather than either action.

## Indicators requiring Board attention

Seven of 24 indicators are red. Four are consequences of the two slipped actions and will clear on the
revised dates. Three warrant Board visibility:

**KRI-10 — AI systems without named owner and authority boundary: 5 (red above 2).** The 60-day
registration deadline the Board approved expires next month. Five systems remain unregistered, of which
two are shadow AI in Finance and Marketing. Under the approved policy these are disabled on expiry.
**The Board should expect business objection when that happens**, and should decide now whether it will
hold the line.

**KRI-13 — Critical services with untested recovery: 6 of 9 (red above 2).** The resilience assessment
established that six services cannot recover within business tolerance and eight of nine had never been
tested. Testing has since begun. Aggregate business impact reaches CAD 7.81M at 72 hours against a
CAD 515,000 improvement programme, of which the first CAD 34,000 addresses every critical finding from the
ransomware exercise.

**KCI-01 — Controls rated Effective: 12% (red below 60%).** At baseline this was 0%. The figure is
genuinely poor and genuinely improving. It is reported because a rising number from a bad start is more
informative than a comfortable one, and because the Board should understand that most of the exposure
reduction to date has come from making existing controls operate rather than buying new ones.

## Acceptances in force

| Ref | Risk | Residual | Authority | Expires | Status |
| --- | --- | :-: | --- | --- | --- |
| ACC-01 | Supplier concentration | 10 | Procurement Director | Month 12 | Holding |
| ACC-02 | Ransomware to plant systems | 10 | CISO | **Month 6** | **Expiring — decision required** |
| ACC-03 | Supplier failure and breach | 10 | Procurement Director | Month 6 | Holding |
| ACC-04 | Workload identity governance | 10 | CIO | Month 6 | Holding |
| ACC-05 | Recovery exceeds tolerance | 10 | COO | **Month 6** | **Expiring — see below** |

**ACC-05 requires amendment, not renewal.** It was accepted on compensating controls that were assumed.
The ransomware tabletop tested three of them — Active Directory recovery, backup usability, recovery
sequencing — and found all three wanting. The acceptance was sound as a decision and optimistic as an
estimate. Recommended: renew conditional on the first resilience wave completing, with a monitoring
indicator attached, which it currently lacks.

## Emerging risk

**AI adoption continues to outpace governance.** Two systems entered production this quarter without
passing registration. The control exists and is not being followed, which is a different problem from not
having a control and requires a different response — enforcement rather than investment.

**One AI system is high-risk under the EU AI Act.** The CV screening tool operates in recruitment for the
Poland business with no human review of rejections and no record of why any candidate was rejected.
Automated rejection has been suspended. Northstar cannot establish whether discriminatory outcomes
occurred during the eighteen months it ran, because no decision records were retained.

## What this report cannot tell you

The technology asset inventory has an estimated 14% coverage gap, concentrated in SaaS acquired outside IT
procurement and AI tooling built on Power Platform. **Every completeness claim in this report is bounded by
that figure.** Unidentified scenarios exist, most probably in shadow SaaS.

This is also the dependency behind both slipped actions, which is why closing it is the single
recommendation below.

---

## Decisions requested

1. **Confirm the AI registration deadline will be enforced**, including disablement of unregistered
   systems, and accept the business disruption that follows.
2. **Approve amendment of ACC-05** rather than renewal — conditional on wave completion, with a monitoring
   indicator attached.
3. **Note the expiry of ACC-02** and that the underlying IT/OT segmentation investment remains deferred to
   FY27, now supported by quantified impact evidence.
4. **Approve funding for asset discovery** to close the inventory gap. It bounds the completeness of all
   risk reporting and is the common dependency behind both delivery slips.
