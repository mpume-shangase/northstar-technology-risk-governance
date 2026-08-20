# Executive Recommendation — AI Governance

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).

**To:** Technology Risk Committee, for onward recommendation to the Board
**From:** Technology Risk
**Subject:** AI governance and emerging technology risk assessment
**Classification:** Internal — Committee

---

## The position

Northstar operates **14 AI systems**. Twelve have no documented authority boundary. Two have no owner at
all. Seven produce no log of what they did. Nine process personal data.

The Board approved AI investment on a business case. **No corresponding risk decision was ever taken.**
Appetite for emerging technology is *open but bounded* — the appetite exists, the bounds were never
implemented.

Sixteen risk scenarios carry aggregate inherent exposure of **218**, seven above appetite and three
Critical. Treatment reduces this to **92, a 58% reduction**, with none above appetite.

## What the Committee has not seen before

**Six of the sixteen scenarios were invisible to the enterprise assessment** completed three months ago:
bias, prompt injection, model drift, oversharing amplification, agent chaining and silent model failure.
These are not new risks that emerged since — they were present and the method could not see them. AI
systems fail differently from conventional systems, and conventional assessment asks the wrong questions.

The defining difference is **silent failure**. A database that goes down announces itself. A forecasting
model that quietly degrades produces confident numbers that inform inventory decisions for months.

## Three findings requiring a decision

**1. The CV screening tool is a high-risk AI system operating without any of the required controls.**
*(AI-02, AI-12)*

TalentFilter screens candidates for shortlisting. Under the EU AI Act, employment and worker selection is
explicitly high-risk, and Northstar processes EU-resident applicant data through its Poland operation.

It operates at Delegated autonomy with **no human review of rejections** and no record of why any
candidate was rejected. If a rejected applicant asks for a reason, Northstar cannot give one. If a pattern
of discriminatory outcomes exists, Northstar cannot detect it — and equally cannot disprove it.

Nobody classified this as an AI system because it was procured as recruitment software.

**2. Shadow AI is already carrying Northstar's commercial position outside the organisation.** *(AI-01)*

The only scenario scored Likelihood 5 — already occurring. Network telemetry shows regular traffic to
consumer AI services from Finance and Sales, with no technical control and no record of what has been
submitted. Northstar cannot state what has left, which means it cannot assess the consequence.

**3. Enabling Copilot broadly before fixing oversharing amplifies an existing problem.** *(AI-10)*

Copilot respects existing permissions — which is exactly the problem. Content that was technically
accessible but practically undiscoverable becomes findable in seconds. Northstar has 1,900 groups, roughly
600 with no recorded owner. **Oversharing remediation must precede broad Copilot enablement**, not follow
it.

## Recommendations

1. **Approve mandatory AI system registration.** No AI system operates in production without a named
   owner, a documented authority boundary and defined logging. Systems unregistered after 60 days are
   disabled. This implements appetite conditions the Board has already approved.

2. **Classify TalentFilter as high-risk and suspend automated rejection immediately.** Require human review
   of every rejection, an explainability record per decision, and vendor bias-testing evidence within 90
   days. If the vendor cannot provide it, replace the tool.

3. **Block unapproved consumer AI services at egress within 30 days**, with a sanctioned alternative
   available first and an amnesty communication rather than an enforcement announcement. The objective is
   redirection, not punishment — blocking without an alternative produces circumvention, not compliance.

4. **Sequence Copilot oversharing remediation ahead of broader enablement.** Access review of high-risk
   sites, sensitivity labelling, and group ownership remediation.

5. **Adopt authority boundaries as a standing control** for all A1 and above systems, enforced in identity
   and API scope rather than in prompts. A boundary that exists only in a prompt is advisory to the model,
   not a control.

6. **Add AI clauses to standard procurement**: prohibition on training use of Northstar data, sub-processor
   pinning, incident notification, and conformity evidence where high-risk. This closes AI-07 across all
   future vendors rather than one at a time.

## What the Committee is being asked to accept

**AI-03 remains at residual 10** — the highest residual in this assessment. Agent identity governance can
be inventoried and scoped manually, but full lifecycle governance for workload identities requires
licensing deferred to FY27 under acceptance ACC-04. Manual quarterly review is the compensating control,
and manual controls do not reduce likelihood below 2.

**Bias in TalentFilter has not been independently tested.** The finding rests on the *absence* of vendor
testing evidence, not on measured disparate outcomes. Northstar cannot currently test it, because no
decision records are retained. Recommendation 2 creates the records that would make future testing
possible — but it does not tell the Committee whether harm has already occurred over the eighteen months
the tool has been running.

That is the uncomfortable part of this assessment and it should not be smoothed over.

---

**Decisions requested:** approve mandatory registration with the 60-day deadline · suspend automated
rejection in TalentFilter and classify as high-risk · approve egress blocking with sanctioned alternative ·
sequence oversharing remediation before Copilot expansion · adopt authority boundaries as a standing
control · approve AI procurement clauses · note residual acceptance on AI-03 and the untestable history on
AI-02.
