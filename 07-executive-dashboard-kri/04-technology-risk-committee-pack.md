# Technology Risk Committee — Monthly Pack

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**Meeting:** Month 6 · **Chair:** Chief Risk Officer · **Papers circulated:** 5 working days in advance
Charter and standing agenda: [Project 01](../01-governance-framework/04-risk-committee-charter.md)

---

## 1. Prior actions

| Action | Owner | Due | Status |
| --- | --- | --- | --- |
| Complete EDR deployment | CISO | Week 10 | **Slipped to Week 16** — dependent on asset inventory |
| EOL system remediation plan | CIO | Week 20 | **Slipped to Week 26** — same dependency |
| AI system registration | CIO | Week 8 | 9 of 14 complete; deadline expires this month |
| Vendor conditions precedent — Cadence | Procurement Director | Week 12 | Complete; CP-1 to CP-7 evidenced before signature |
| Restore testing, all critical services | COO | Week 8 | Complete; 9 of 9 passed |

**Decision required:** accept revised dates for the two slipped actions, or reallocate resource to hold
the original.

## 2. Aggregate exposure

| | Q1 | Q2 | Movement |
| --- | :-: | :-: | :-: |
| Aggregate exposure | 330 | 271 | −59 (−18%) |
| Above appetite | 13 | 9 | −4 |
| Critical | 3 | 0 | −3 |
| Against plan | — | +12 | 4.6% behind |

Reduction is real but behind schedule. The variance traces entirely to the two slipped actions above, both
blocked on the same dependency.

## 3. Risks above appetite

| ID | Scenario | Inherent | Current | Treatment status | Owner |
| --- | --- | :-: | :-: | --- | --- |
| CYB-02 | Ransomware halts production | 15 | 15 | Blocked — EDR gap; segmentation deferred ACC-02 | CISO |
| CYB-03 | Unpatched internet-facing exploit | 16 | 8 | On track | CISO |
| CYB-05 | Phishing to business email compromise | 16 | 12 | On track — simulation programme starting | CISO |
| CLD-01 | Cloud misconfiguration exposes data | 15 | 15 | On track — scanning deploys Week 14 | CIO |
| DAT-01 | Personal data retained unlawfully | 16 | 16 | At risk — depends on data inventory | CCO |
| TPR-01 | SaaS outage halts order processing | 15 | 15 | On track — fallback documented Week 16 | Procurement |
| TPR-02 | Supplier breach exposes data | 15 | 15 | On track | Procurement |
| EMT-03 | Workload identities over-permissioned | 20 | 10 | Treated; residual accepted ACC-04 | CIO |
| RES-01 | Recovery exceeds tolerance | 15 | 15 | On track — Wave 1 in progress | COO |

**Decision required:** CYB-02 cannot reduce further while segmentation is deferred and the EDR gap
persists. Committee to confirm whether the ACC-02 acceptance is renewed on expiry or escalated to the
Audit & Risk Committee for capital reconsideration.

## 4. Indicator dashboard

| Status | Count | Indicators |
| --- | :-: | --- |
| 🔴 Red | 7 | KRI-07, KRI-08, KRI-09, KRI-10, KRI-13, KRI-16, KCI-01 |
| 🟡 Amber | 6 | KRI-01, KRI-02, KRI-15, KRI-18, KPI-01, KPI-02 |
| 🟢 Green | 11 | |

### Reds requiring direction

**KRI-10 — AI systems without owner and boundary: 5.** Registration deadline expires this month. Two are
shadow AI. Under approved policy they are disabled on expiry. Committee should anticipate business
objection and decide its position before the date, not after.

**KRI-09 — Critical suppliers without current due diligence: 4.** Reassessment cycle began Week 14; four
of eleven remain. Vendor Manager reports capacity constraint, not vendor resistance.

**KRI-16 — EOL systems without remediation plan: 14.** Blocked on the same asset inventory dependency.

**KCI-01 — Controls rated Effective: 12%.** From a baseline of 0%. Trajectory is correct; the absolute
number remains poor and should not be presented as success.

## 5. New and emerging risks

| Proposed | Scenario | Proposed score | Recommendation |
| --- | --- | :-: | --- |
| NEW-01 | If AI systems continue entering production without registration, governance controls approved by the Board may be routinely bypassed, undermining the control framework itself | 12 | Accept into register — this is a control-integrity risk distinct from the AI risks already held |
| NEW-02 | If the asset inventory gap persists, risk identification remains demonstrably incomplete and reporting understates exposure by an unknown margin | 15 | Accept into register above appetite; escalate to ARC with funding request |

NEW-02 deserves the Committee's attention. It is the only risk in the register whose consequence is that
**the register itself is wrong**. It is also the common dependency behind both delivery slips this period.

## 6. Acceptances

| Ref | Expires | Recommendation |
| --- | --- | --- |
| ACC-02 | This month | Renew for 6 months, or escalate for capital reconsideration |
| ACC-05 | This month | **Amend, not renew** — condition on Wave 1 completion; attach KRI-13 as monitoring, which it currently lacks |
| ACC-01, ACC-03, ACC-04 | Month 12 / Month 6 | Holding; no action |

## 7. Escalations to the Audit & Risk Committee

1. NEW-02 — asset inventory gap, above appetite, funding request
2. ACC-02 expiry and the deferred segmentation investment
3. KRI-10 — AI registration enforcement and expected business disruption
4. KCI-01 — control effectiveness at 12%, with trajectory

---

**Chair's note.** Three of nine above-appetite risks are blocked rather than progressing, and all three
trace to dependencies outside their own treatment plans. The Committee should resist re-dating them
individually and instead direct the dependency — which is the substance of escalation 1.
