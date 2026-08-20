# Executive Risk Assessment — Summary

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**To:** Audit & Risk Committee · **From:** Technology Risk
**Subject:** Enterprise technology risk assessment — findings
**Classification:** Internal — Committee

---

## Answer to the question you asked

In March the Committee asked what Northstar's total technology risk exposure is, and how much sits above
appetite. The answer:

**Twenty-four risk scenarios carry an aggregate inherent exposure of 330. Thirteen of them — 54% — breach
the Board's appetite threshold of 15. Three are Critical.**

More significant than any single number: **of 24 scenarios, not one existing control was assessed as
Effective.** Eleven were partially effective, twelve ineffective, one absent. Northstar is not
uncontrolled — it has policies, tooling and process. It is *unassured*: controls exist on paper and
cannot be evidenced as operating.

## The three Critical scenarios

**CYB-01 — Credential compromise enabling fraudulent payment (20).** MFA is registered by 71% of users
and enforced by policy for none. There is no detection of segregation-of-duties conflict in finance
entitlements. A single credential can reach payment authorisation.

**EMT-03 — Workload identities holding unreviewed directory permissions (20).** 340 service principals
exist; six hold broad directory permissions granted during a 2025 pilot and never revisited. These
identities have no owner, no expiry and no review, and no joiner-mover-leaver process will ever disable
them. Confirmed by directory enumeration, not projection.

**EMT-02 — Confidential data disclosed via unapproved AI tools (20).** The only scenario scored
Likelihood 5 — already occurring. Network sampling shows regular traffic to consumer AI services from
Finance and Sales endpoints, with no technical control and no record of what has been submitted.

## What the profile reveals about sequencing

Seven of the top ten scenarios depend on the same underlying condition: **an identity, human or
non-human, holds access nobody reviews.** Treating them as separate problems would fund four programmes.
Treating the common condition funds one.

Equally: **66% of aggregate exposure originates in internal control weakness** — not external threat, not
vendor dependency. Most of Northstar's exposure is addressable by internal decision, without
renegotiating a contract or reducing a threat we do not control.

## Emerging technology is the fastest-moving concentration

Four AI scenarios carry 20% of total exposure — the highest exposure per scenario of any category.
Northstar has been deploying AI for eighteen months and governing it for none. The Committee approved AI
investment on a business case; no corresponding risk decision was ever taken.

This is not an argument against AI adoption. Board appetite for emerging technology is *open but
bounded* — the bounds simply have not been implemented. Four conditions were set in the appetite
statement: named owner, defined authority boundary, human review of consequential decisions, monitoring.
None is currently in place for any AI system in production.

## What this assessment cannot tell you

- **Residual risk.** This register is inherent-only. Residual scoring follows control testing in the next
  phase. Any residual figure quoted today would be an estimate presented as a measurement.
- **Complete coverage.** The asset inventory has an estimated 12–18% gap, concentrated in SaaS bought
  outside IT procurement and AI tooling on Power Platform. Unidentified scenarios exist.
- **Independently challenged scores.** Assessment was performed by a single assessor. Second-line
  challenge is scheduled at the next Technology Risk Committee; until then scores are proposed, not
  agreed.

## Recommendations to the Committee

1. **Note** that 13 scenarios breach appetite and require formal treatment or time-boxed acceptance under
   the escalation thresholds in the appetite statement.
2. **Direct** that the three Critical scenarios enter treatment planning immediately; Critical risk cannot
   be a resting state under Board appetite.
3. **Commission** control effectiveness testing (Project 03) to establish residual position before
   treatment funding is finalised.
4. **Approve** the asset discovery activity required to close the inventory gap — assessment completeness
   is bounded by it, and tolerance T-09 is currently amber.
5. **Require** that every AI system in production be registered with a named owner and documented
   authority boundary within 60 days, or be withdrawn — implementing appetite conditions the Committee
   has already approved.

---

**Decisions requested:** note the exposure position · direct Critical scenarios into treatment planning ·
commission control testing · approve asset discovery · set the 60-day AI registration deadline.
