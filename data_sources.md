# Data Sources — Opioid Ecosystem Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Opioid Ecosystem: Prescription Ratchet) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_mortality_morbidity`

68,630 overdose deaths × geometric mean VSL ($9.5M EPA/DOT) = $636B mortality + $196B morbidity (2.7M OUD × $145K QALY loss, 50% discounted). Range: DOT VSL ($508B) to EPA VSL ($987B). Sources: CDC WONDER, EPA VSL, CEA 2017.

*Full citations: paper §4 (available SSRN).*

### `C2_healthcare_burden`

ED/inpatient ($27.2B), NAS ($0.6B), infectious disease (Hep C + HIV). Pew estimate $35B (direct costs) to Cornell $89.1B (broader utilization). Sources: Pew Charitable Trusts, Weill Cornell 2018, CDC.

*Full citations: paper §4 (available SSRN).*

### `C3_labor_market`

LFPR loss $110B (Krueger 2017, 2M displaced workers × $55K), absenteeism/presenteeism $42B, incarceration productivity $8B. 20% overlap discount applied. Sources: Krueger 2017, Florence 2021, BLS.

*Full citations: paper §4 (available SSRN).*

### `C4_criminal_justice_child_welfare`

Criminal justice $14.8B (police $6.2B, corrections $5.4B, courts), child welfare $2.8B (foster care $1.6-1.9B, CPS $0.9B). Sources: Pew, HHS, Florence 2021.

*Full citations: paper §4 (available SSRN).*

### `C5_community_capital`

Property value destruction $22B/yr (Custodio 2021, 0.5-1.5% national housing stock), fiscal revenue loss $5B, entrepreneurship loss $7.5B. Sources: Custodio et al. 2021.

*Full citations: paper §4 (available SSRN).*

### `C6_governance_institutional_failure`

Marino Bill enforcement gap $20-36B, lobbying DWL $3-5B, institutional trust erosion $5-10B, CME corruption $5-8B. $880M lobbying (2006-2015). Sources: AP/CPI, Washington Post, DOJ.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $75.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Opioid Ecosystem (Prescription Ratchet)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
