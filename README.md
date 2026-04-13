# SAPM Monte Carlo — Deep-Sea Mining / Abyssal Recovery Floor

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Deep-Sea Mining (Abyssal Recovery Floor).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **6.9** |
| β_W mean | 7.05 |
| β_W std | 1.39 |
| **90% CI** | **[5.0, 9.6]** |
| 99% CI | [4.4, 11.0] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$34.5B/yr** |
| Π (revenue) | $5.0B/yr |

**β_W = 6.9** means the deep-sea mining industry destroys **$6.9 in system
welfare for every $1.00 in revenue** — across 5 channels and 100,000 Monte Carlo draws.

**Classification**: Class 1 — Impossibility

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
git clone https://github.com/epostnieks/sapm-mc-deep-sea-mining.git
cd sapm-mc-deep-sea-mining
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 6.9` and `ΔW median : $34.5B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_environmental_damage | $13.6B | [$8.2B, $22.3B] | Lognormal |
| C2_health_externality | $8.5B | [$5.2B, $14.0B] | Lognormal |
| C3_climate_cost | $6.8B | [$5.4B, $8.2B] | Normal |
| C4_ecosystem_degradation | $3.4B | [$2.1B, $5.6B] | Lognormal |
| C5_governance_capture | $1.7B | [$1.0B, $2.8B] | Lognormal |
| **Total ΔW** | **$34.5B** | **[$25.2B, $47.8B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 3.7 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0300%**
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

> Postnieks, E. (2026). *SAPM Monte Carlo — Deep-Sea Mining (Abyssal Recovery Floor)*.
> GitHub: epostnieks/sapm-mc-deep-sea-mining.
> https://github.com/epostnieks/sapm-mc-deep-sea-mining
