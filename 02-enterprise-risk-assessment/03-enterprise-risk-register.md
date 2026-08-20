# Enterprise Technology Risk Register

> ⚠️ Constructed case study. See [`../00-programme/disclaimer.md`](../00-programme/disclaimer.md).
> Machine-readable source: [`02-enterprise-risk-register.csv`](./02-enterprise-risk-register.csv) — full
> column set including causal driver, business objective, control effectiveness and evidence basis.

**24 scenarios · 8 categories · inherent scoring only** (residual follows control testing in Project 03).
Method: [`01-assessment-methodology.md`](./01-assessment-methodology.md).

---

## Position

| Measure | Value |
| --- | --- |
| Scenarios assessed | 24 |
| Aggregate inherent exposure | **330** |
| Above appetite (≥15) | **13 of 24 — 54%** |
| Critical (20–25) | 3 |
| Existing controls rated *Effective* | **0 of 24** |
| Estimated asset inventory coverage gap | 12–18% |

![Enterprise technology risk heat map](./assets/enterprise-heat-map.svg)

## Exposure by category

| Category | Scenarios | Exposure | Share | Above appetite |
| --- | :-: | :-: | :-: | :-: |
| Cybersecurity | 5 | 82 | 25% | 5 |
| Emerging Technology / AI | 4 | 67 | 20% | 3 |
| Data | 3 | 40 | 12% | 1 |
| Third Party | 3 | 40 | 12% | 2 |
| Cloud & Infrastructure | 3 | 32 | 10% | 1 |
| Resilience | 2 | 25 | 8% | 1 |
| Technology Operations | 2 | 24 | 7% | 0 |
| Compliance & Regulatory | 2 | 20 | 6% | 0 |
| **Total** | **24** | **330** | | **13** |

Emerging Technology carries 20% of exposure from four scenarios — the highest exposure *per scenario* of
any category. Northstar has been deploying AI for eighteen months and governing it for none.

---

## Top 10 risk profile

Ranked by inherent score, then by proximity of impact to customer or regulatory consequence.

| Rank | ID | Scenario | Cat | L | I | Score | Owner |
| :-: | --- | --- | --- | :-: | :-: | :-: | --- |
| 1 | CYB-01 | Credential compromise enables fraudulent vendor payment | Cyber | 4 | 5 | **20** | CISO |
| 2 | EMT-03 | Workload identities and AI agents hold unreviewed directory-wide permissions | AI | 4 | 5 | **20** | CIO |
| 3 | EMT-02 | Confidential data disclosed via unapproved public AI tools | AI | 5 | 4 | **20** | CIO |
| 4 | CYB-03 | Unpatched internet-facing system exploited for initial access | Cyber | 4 | 4 | 16 | CISO |
| 5 | DAT-01 | Personal data retained beyond lawful basis | Data | 4 | 4 | 16 | CCO |
| 6 | CYB-05 | Phishing leads to business email compromise | Cyber | 4 | 4 | 16 | CISO |
| 7 | CYB-02 | Ransomware halts multi-site production | Cyber | 3 | 5 | 15 | CISO |
| 8 | TPR-01 | Critical SaaS outage halts customer order processing | 3rd party | 3 | 5 | 15 | Procurement Dir. |
| 9 | RES-01 | Recovery exceeds maximum tolerable disruption | Resilience | 3 | 5 | 15 | COO |
| 10 | EMT-01 | AI agent acts outside authority boundary on financial systems | AI | 3 | 5 | 15 | CIO |

Also above appetite: CYB-04 (15), CLD-01 (15), TPR-02 (15).

### What the top 10 has in common

Seven of the ten are enabled by the same underlying condition: **an identity — human or non-human — holds
access that nobody is reviewing.** CYB-01, CYB-04 and EMT-03 are that condition directly; CYB-05, TPR-02,
CLD-01 and EMT-01 depend on it to convert an initial foothold into loss.

This is the finding that changes investment sequencing. Treating those scenarios separately would fund
four programmes; treating the common condition funds one. That analysis is carried into Project 03.

### The AI scenarios are not hypothetical

EMT-02 is the only scenario in the register scored Likelihood 5 — *already occurring*. Network telemetry
sampling showed regular traffic to consumer AI services from Finance and Sales endpoints, with no
technical control and no record of what was submitted. EMT-03 was confirmed by directory enumeration:
340 workload identities, of which six hold broad directory permissions granted during a 2025 pilot and
never reviewed. Neither is a projection.

---

## Full register

| ID | Scenario (abbreviated) | Category | Driver | L | I | Score | Band | Owner |
| --- | --- | --- | --- | :-: | :-: | :-: | --- | --- |
| CYB-01 | Credential compromise → fraudulent payment | Cybersecurity | Internal control | 4 | 5 | **20** | Critical | CISO |
| CYB-02 | Ransomware halts multi-site production | Cybersecurity | External threat | 3 | 5 | **15** | High | CISO |
| CYB-03 | Unpatched internet-facing system exploited | Cybersecurity | External threat | 4 | 4 | **16** | High | CISO |
| CYB-04 | Standing privileged account compromised | Cybersecurity | Internal control | 3 | 5 | **15** | High | CISO |
| CYB-05 | Phishing → business email compromise | Cybersecurity | External threat | 4 | 4 | **16** | High | CISO |
| CLD-01 | Misconfigured cloud storage exposes data | Cloud | Internal control | 3 | 5 | **15** | High | CIO |
| CLD-02 | Regional outage, no tested failover | Cloud | External dependency | 2 | 4 | 8 | Moderate | CIO |
| CLD-03 | Unmanaged capacity and cost growth | Cloud | Internal control | 3 | 3 | 9 | Moderate | CIO |
| DAT-01 | Personal data retained beyond lawful basis | Data | Internal control | 4 | 4 | **16** | High | CCO |
| DAT-02 | Data processed outside approved jurisdiction | Data | Internal control | 3 | 4 | 12 | Moderate | CCO |
| DAT-03 | Master data quality undermines reporting | Data | Internal control | 3 | 4 | 12 | Moderate | CIO |
| TPR-01 | Critical SaaS outage halts order processing | Third Party | External dependency | 3 | 5 | **15** | High | Procurement |
| TPR-02 | Supplier breach exposes Northstar data | Third Party | External dependency | 3 | 5 | **15** | High | Procurement |
| TPR-03 | Concentration across ERP, identity and email | Third Party | External dependency | 2 | 5 | 10 | Moderate | Procurement |
| EMT-01 | AI agent acts outside authority boundary | Emerging Tech | Internal control | 3 | 5 | **15** | High | CIO |
| EMT-02 | Confidential data into unapproved public AI tools | Emerging Tech | Internal control | 5 | 4 | **20** | Critical | CIO |
| EMT-03 | Workload identities hold unreviewed permissions | Emerging Tech | Internal control | 4 | 5 | **20** | Critical | CIO |
| EMT-04 | AI output relied on without human verification | Emerging Tech | Internal control | 4 | 3 | 12 | Moderate | CIO |
| OPS-01 | Unauthorised change causes outage | Tech Ops | Internal control | 3 | 4 | 12 | Moderate | CIO |
| OPS-02 | End-of-life systems unsupported | Tech Ops | Internal control | 3 | 4 | 12 | Moderate | CIO |
| RES-01 | Recovery exceeds maximum tolerable disruption | Resilience | Internal control | 3 | 5 | **15** | High | COO |
| RES-02 | Backup restore fails at point of need | Resilience | Internal control | 2 | 5 | 10 | Moderate | COO |
| REG-01 | Regulatory notification missed or late | Regulatory | Internal control | 2 | 4 | 8 | Moderate | CCO |
| REG-02 | Cannot evidence controls to customers | Regulatory | Internal control | 3 | 4 | 12 | Moderate | CCO |

**Bold** scores breach the Board appetite threshold of 15.

## Causal driver analysis

| Driver | Scenarios | Exposure | Share |
| --- | :-: | :-: | :-: |
| Internal control weakness | 16 | 218 | 66% |
| External dependency | 5 | 63 | 19% |
| External threat | 3 | 47 | 14% |

**Two-thirds of exposure originates in controls Northstar already owns and can fix without a third party's
cooperation.** That is the most commercially useful line in this assessment — it means most of the
exposure is addressable through internal decision rather than vendor negotiation or threat reduction.

## Where this register is weakest

Stated plainly so the Committee can weight it accordingly:

- **Likelihood calibration for AI scenarios.** The technology is too new for reliable base rates. EMT
  scores rest on observed internal conditions rather than external frequency data.
- **No independent challenge yet.** Scored by a single assessor; second-line challenge is scheduled at
  the next Technology Risk Committee. Until then, treat scores as proposed rather than agreed.
- **Asset inventory gap of 12–18%** means unidentified scenarios exist, most likely in shadow SaaS.
- **Impact estimates for production disruption** came from Operations without independent validation.
