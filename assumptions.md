# Monte Carlo Assumptions — Opioid Ecosystem / Prescription Ratchet

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $75.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 14.96 | Confirmed by N=100,000 draws |
| ΔW median (result) | $1,121.9B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_mortality_morbidity` | lognormal | $508.0B | $832.0B | $987.0B | 68,630 overdose deaths × geometric mean VSL ($9.5M EPA/DOT) = $636B mortality +  |
| `C2_healthcare_burden` | lognormal | $35.0B | $62.0B | $89.0B | ED/inpatient ($27.2B), NAS ($0.6B), infectious disease (Hep C + HIV). Pew estima |
| `C3_labor_market` | normal | $76.0B | $128.0B | $168.0B | LFPR loss $110B (Krueger 2017, 2M displaced workers × $55K), absenteeism/present |
| `C4_criminal_justice_child_welfare` | lognormal | $12.0B | $17.6B | $25.0B | Criminal justice $14.8B (police $6.2B, corrections $5.4B, courts), child welfare |
| `C5_community_capital` | lognormal | $16.0B | $34.5B | $55.0B | Property value destruction $22B/yr (Custodio 2021, 0.5-1.5% national housing sto |
| `C6_governance_institutional_failure` | normal | $35.0B | $45.0B | $55.0B | Marino Bill enforcement gap $20-36B, lobbying DWL $3-5B, institutional trust ero |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 6.9 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 6.9) = 0.0000%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 14.92 | 20% DC adj = 11.94 | 40% DC adj = 8.95

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $1,122B = 1.1% of world GDP ($106T) ✓
- **β_W range**: 14.96 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
