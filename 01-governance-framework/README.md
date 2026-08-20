# Project 01 — Technology Risk Governance Framework

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**CRISC Domain 1 — Governance (26%)**
**Role played:** Technology Risk & Governance Consultant · **Duration modelled:** 8 weeks

---

## The problem

Northstar Global runs technology risk in five places and reconciles it in none. Cybersecurity keeps a
threat register, IT Operations tracks incidents, the AI steering group lists pilots, Finance owns IT
controls for financial reporting, Compliance maintains a regulatory matrix.

Each is competent. Collectively they cannot answer what the Board asked in March: **what is our total
technology risk exposure, and how much of it is above what we are willing to carry?**

## What I built

| Artefact | What it decides |
| --- | --- |
| [Governance framework](./01-governance-framework.md) | Structure, three-lines accountability, risk taxonomy, policy hierarchy, lifecycle |
| [Risk appetite & tolerance statement](./02-risk-appetite-and-tolerance.md) | Board appetite by category, 10 tolerance thresholds, escalation bands |
| [Risk ownership matrix](./03-risk-ownership-matrix.md) | Risk owner vs control owner vs action owner; lifecycle RACI; contested ownership |
| [Committee charter](./04-risk-committee-charter.md) | TRC mandate, membership, quorum, delegated authority, standing agenda, effectiveness measures |

## The four decisions worth defending in an interview

**1. Appetite varies by category.** A single organisational appetite forces the same threshold onto
ransomware and a print server, which is why most appetite statements go unused. Cybersecurity and privacy
are averse; emerging technology is *open but bounded*.

**2. AI appetite is "open, bounded," not zero.** An organisation declaring zero appetite for AI risk while
deploying AI has written a statement its own staff will route around. The honest position states the
appetite and constrains it with four testable conditions — named owner, defined authority boundary, human
review of consequential decisions, monitoring. Each becomes a control in Domain 3.

**3. The TRC is chaired by the CRO, not the CIO.** A committee chaired by the executive accountable for
delivering the technology is being asked to challenge itself.

**4. Resilience is owned by the COO, not the CIO.** The consequence of an outage is unfulfilled customer
orders. If the CIO owns it, resilience investment competes against other IT priorities inside one budget
rather than being demanded by the business that absorbs the loss.

## What the framework admits it cannot do

The framework depends on an accurate technology asset inventory. Northstar's is incomplete — particularly
for SaaS bought outside IT procurement and for AI tooling built on Power Platform. Risk identification is
therefore demonstrably incomplete at launch.

Rather than assume this away, inventory coverage is a Board-level tolerance (T-09, red above 15% gap), and
three ownership disputes are recorded as unresolved in the ownership matrix. A governance framework that
claims complete coverage on day one is describing an organisation that does not exist.

## Feeds

Appetite thresholds and the taxonomy defined here are used by every subsequent project.
Escalation bands are the same ones applied in
[Project 02 — Enterprise Risk Assessment](../02-enterprise-risk-assessment/).
