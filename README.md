# SAPM Monte Carlo — Opioid Ecosystem / Prescription Ratchet

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Opioid Ecosystem (Prescription Ratchet).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **14.96** |
| β_W mean | 15.02 |
| β_W std | 1.51 |
| **90% CI** | **[12.6, 17.6]** |
| 99% CI | [11.8, 18.8] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$1,121.9B/yr** |
| Π (revenue) | $75.0B/yr |

**β_W = 14.96** means the opioid ecosystem industry destroys **$14.96 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 2 — Intractability

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-opioids.git
cd sapm-mc-opioids
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 14.96` and `ΔW median : $1,121.9B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_mortality_morbidity | $831.5B | [$700.5B, $986.4B] | Lognormal |
| C2_healthcare_burden | $62.0B | [$43.1B, $89.2B] | Lognormal |
| C3_labor_market | $128.0B | [$82.0B, $173.9B] | Normal |
| C4_criminal_justice_child_welfare | $17.6B | [$12.4B, $25.0B] | Lognormal |
| C5_community_capital | $34.4B | [$21.7B, $54.8B] | Lognormal |
| C6_governance_institutional_failure | $45.0B | [$35.0B, $55.0B] | Normal |
| **Total ΔW** | **$1,121.9B** | **[$948.5B, $1,320.6B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 6.9 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0000%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Opioid Ecosystem (Prescription Ratchet)*.
> GitHub: epostnieks/sapm-mc-opioids.
> https://github.com/epostnieks/sapm-mc-opioids
