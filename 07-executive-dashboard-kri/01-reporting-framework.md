# Risk Reporting Framework

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**CRISC Domain 3 — Risk Response & Reporting (32%)**

---

## 1. Why reporting fails

Most technology risk reporting fails in one of three ways, and all three are design faults rather than
effort faults:

| Failure | Symptom | Cause |
| --- | --- | --- |
| **Reports data, not decisions** | Executives receive counts and percentages and take no action | No indicator is tied to a threshold that obliges someone to do something |
| **Permanently red** | Dashboards show red for months; executives stop reading | Thresholds set at aspiration rather than at the current treated baseline |
| **Same pack for every audience** | Board receives operational detail; engineers receive strategic summary | One artefact, three audiences, none served |

This framework is designed against those three.

## 2. Audience layering

| Forum | Frequency | Question they are answering | Content |
| --- | --- | --- | --- |
| **Board** | Quarterly | Are we within the risk appetite we set? | Aggregate exposure vs appetite, movement, above-appetite scenarios, acceptances, emerging risk. One page. |
| **Audit & Risk Committee** | Quarterly | Is risk being managed, and is the framework working? | Board content plus control effectiveness, overdue treatment, KRI reds, assurance coverage |
| **Technology Risk Committee** | Monthly | What decisions are needed this month? | Full register movement, all indicators, treatment status by owner, new and emerging risks |
| **Control and risk owners** | Monthly | What do I need to do? | Their own risks, controls, indicators and actions only |

**The Board pack is one page and contains no technology.** If a Board paper requires the reader to know
what a service principal is, it is the wrong paper. The Board sets appetite and holds management to it;
that is the entire conversation.

## 3. KRI, KCI and KPI

These are routinely conflated, which is why dashboards fill with numbers nobody acts on. They answer
different questions and drive different responses.

| | Question | Example | Response on breach |
| --- | --- | --- | --- |
| **KRI** — Key Risk Indicator | Is a risk becoming more likely? | Endpoints without EDR coverage | Escalate per the risk's residual band |
| **KCI** — Key Control Indicator | Is the control operating as designed? | Controls rated Effective at last test | Control owner remediates; risk owner informed |
| **KPI** — Key Performance Indicator | Is the programme delivering? | Treatment actions closed by due date | Resourcing conversation, not a risk escalation |

**Only KRI breaches escalate as risk.** A KPI breach is a delivery problem — real, but it belongs in a
different conversation, and routing it through risk escalation trains executives to discount escalations.

Northstar's catalogue holds 18 KRIs, 4 KCIs and 2 KPIs. The imbalance is deliberate at this stage: control
effectiveness is measured quarterly on a testing cycle, so KCIs cannot be more frequent than the tests
behind them.

## 4. Threshold design

Every indicator has green, amber and red thresholds, and each colour obliges a defined response.

| Band | Meaning | Obligation |
| --- | --- | --- |
| Green | Within tolerance | Continue monitoring |
| Amber | Drifting | Control owner acts; TRC informed at next sitting |
| Red | Outside tolerance | Escalate per residual band; treatment or acceptance decision required |

Three design rules, each learned from a common failure:

**Set thresholds at the treated baseline, not at zero.** KRI-12 (workload identities holding high-privilege
permissions) sits green at 11 — the number remaining after treatment under acceptance ACC-04. Setting it
at zero would show red permanently, which trains the Committee to ignore the dashboard entirely.

**Some indicators have no amber.** KRI-17, missed regulatory notifications, is green at zero and red at
one. There is no meaningful middle state, and inventing one implies tolerance that does not exist.

**A threshold without a defined consequence is decoration.** Each indicator in the catalogue names the
response on breach and the owner who must make it.

## 5. Trend over position

A single-period snapshot cannot distinguish an organisation that has improved from 400 to 271 from one
that has deteriorated from 180 to 271. The same number means opposite things.

Every quantitative measure is therefore reported as **actual against plan across time**, not as a point
value. This is also what makes variance visible: Q2 actual exposure of 271 against a plan of 259 is a 4.6%
overrun that a snapshot would have concealed entirely.

## 6. Reporting the uncomfortable

The framework requires three things to appear in every pack regardless of whether anyone asks:

- **Acceptances approaching expiry.** An acceptance that lapses without a renewal decision converts a
  governed risk into an ungoverned one silently.
- **Assumptions that have not been tested.** ACC-05's compensating controls were assumed until the
  tabletop tested three of them and found them wanting.
- **What the assessment could not see.** The asset inventory gap of 14% bounds every completeness claim
  in the pack.

Reporting that only surfaces good news is not reporting; it is marketing, and executives learn to discount
it within about two cycles.

## 7. Escalation routing

Escalation follows the residual band and the routing defined in
[Project 01](../01-governance-framework/03-risk-ownership-matrix.md). Certain events escalate regardless
of calculated score, because waiting for a reporting cycle would be absurd:

- Any confirmed breach of personal data
- Any AI system acting outside its documented authority boundary
- Any critical supplier entering insolvency or announcing service withdrawal
- Any business process exceeding its maximum tolerable disruption
- Any control failure that was previously reported as effective
- Any risk acceptance reaching expiry without a renewal decision

The fifth is the one most frameworks omit. A control that was reported effective and then fails means the
previous report was wrong — which is a reporting integrity issue as much as a control issue.
