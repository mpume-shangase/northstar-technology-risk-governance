# 08 — Executive Summary

> ⚠️ Constructed case study. Northstar Global is fictional.

**To:** Audit & Risk Committee, Northstar Global
**From:** Identity Risk Lead
**Subject:** Identity risk assessment — findings and recommended treatment
**Classification:** Internal — Committee

---

## Recommendation

Approve CAD 148,000 over 36 weeks to treat fourteen identified identity risk scenarios, eight of which
currently breach the Committee's approved risk appetite. Approve the two documented risk acceptances at
ACC-01 and ACC-02.

## Position

Northstar Global's identity controls were designed for a smaller company. Two acquisitions and 40%
headcount growth in 36 months have not been matched by investment in identity process, and the estate now
carries **eight scenarios above the Committee's stated appetite threshold, three of them Critical**.

The central finding is narrow enough to state in one sentence: **Northstar controls the granting of access
well and the retention of access barely at all.** Every significant gap follows from it — terminated
employees keeping accounts, contractors outliving their contracts, entitlements accumulating after
promotion, and 340 non-human identities that no process has ever reviewed.

## The three findings that require a decision

**1. A credential alone can reach finance data.** MFA is registered by 71% of employees but enforced by
policy for none, and legacy authentication protocols remain open — a route that bypasses conditional
access controls entirely, used 4,180 times in the last 30 days. *(R-06, R-07 — inherent 20 and 16)*

**2. Access outlives employment.** Median time from termination to account disable is nine days. Thirty-four
terminated accounts were still active at the time of assessment, one for 41 days with retained access to
the finance system. No contractor identity carries an expiry date. *(R-01, R-03 — inherent 20 and 16)*

**3. Nobody is governing the non-human identities.** Northstar has 340 workload identities, including two
Copilot agents and four Power Platform connections granted broad directory permissions during a 2025 pilot
and never reviewed. These identities have no owner, no expiry and no review, and no leaver process will
ever disable them. They outnumber the IT department five to one. *(R-08 — inherent 20)*

## Treatment and outcome

| | Before | After treatment |
| --- | --- | --- |
| Aggregate risk score | 202 | 90 |
| Scenarios above appetite | 8 | 0 |
| Critical scenarios | 3 | 0 |
| Permanent Global Administrators | 12 | 2 |
| Policy-enforced MFA | 0% | 100% |
| Median termination-to-disable | 9 days | ≤4 hours |
| Critical apps under certification | 0 of 4 | 4 of 4 |
| Identity Secure Score | 48% | 79% (modelled) |

**Aggregate identity risk reduces by 55%.** Delivery is in three waves over 36 weeks, sequenced so that
the authentication bypass closes in the first eight.

## Commercial case

Modelled exposure from a single identity-driven fraudulent payment incident — including response,
production disruption, regulatory cost and customer remediation — is **CAD 2.1M**. Expected annual loss
before treatment is approximately CAD 630K. Treatment costs CAD 148K and pays for itself if it prevents
one such incident within four years.

If the Committee cannot fund the full programme this cycle, **five actions requiring no capital
expenditure reduce aggregate risk by 37% within 90 days.** These are set out in section 7 and can proceed
under existing licensing and headcount.

## Risks the Committee is being asked to accept

Two residual risks are recommended for formal acceptance rather than treatment, both at Moderate and both
time-boxed to six months with monitoring thresholds and hard escalation triggers:

- **ACC-01 (R-08, residual 10)** — full workload identity governance requires CAD 68,000 of additional
  licensing, deferred to FY27. Partial treatment reduces the scenario from Critical to Moderate at no
  licence cost.
- **ACC-02 (R-13, residual 10)** — 23 pre-existing Segregation of Duties conflicts in finance cannot be
  cleared until the FY27 role redesign, as six have no alternative role holder at the Mexico and Malaysia
  sites. Detective reporting and dual-authorisation apply in the interim.

## What this assessment does not cover

Operational technology identity was excluded from scope beyond the AD-integrated front end. A plausible
IT-to-OT lateral path therefore exists that this assessment cannot speak to. **The Committee should commission
a separate OT identity assessment.** Impact estimates for production disruption were provided by Operations
and not independently validated.

## Assurance and reporting

On approval, fourteen Key Risk Indicators begin monthly collection with quarterly reporting to this
Committee. Residual risk is re-scored at the close of each wave, not asserted at approval. The register is
a living document with named risk owners and control owners against every line.

---

**Decisions requested:** approve treatment funding of CAD 148,000 · approve acceptances ACC-01 and ACC-02 ·
note the OT scope exclusion and commission a separate assessment · confirm quarterly KRI reporting to this
Committee.
