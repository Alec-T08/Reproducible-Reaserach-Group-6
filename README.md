# Replicating *"Who Profits in a Post-American World?"*
**Structural Break Analysis of the U.S. Dollar–Treasury Yield Nexus Under Tariff Shock Conditions**

> Group 6 · Reproducible Research · University of Warsaw · Master's Programme · Semester IV · 2025/2026

---

## What This Project Does

This project replicates and extends the empirical analysis from the *Foreign Affairs* article **"Who Profits in a Post-American World?"** (2025, p. 26), which documents an unusual divergence between the U.S. Dollar Index (DXY) and 10-year U.S. Treasury yields following Trump-era tariff announcements in Spring 2025.

Under normal conditions, the dollar and Treasury yields co-move positively during risk-off episodes. The article argues that the April 2025 tariff shock broke this relationship — yields rose while the dollar fell — a pattern more typical of emerging market stress than a reserve currency country. We test this claim formally using cointegration analysis and dynamic conditional correlation modelling.

**Research question:** Did the "Liberation Day" tariff announcement (April 2, 2025) cause a structural break in the historical co-movement between DXY and 10-year U.S. Treasury yields?

---

## Methodology

Three sequential notebooks implement the full analytical pipeline:

| Notebook | Method | Purpose |
|----------|--------|---------|
| `01_analysis.ipynb` | Descriptive analysis | Time-series visualisation around key tariff event dates |
| `02_cointegration_testing.ipynb` | ADF · Engle-Granger · Johansen | Test for long-run equilibrium pre vs post Liberation Day |
| `03_dcc_garch.ipynb` | DCC-GARCH(1,1) · Event-window analysis | Estimate time-varying correlation ρ(t); Welch t-tests across 90-day, 6-month, 1-year windows |

---

## Requirements

- Python >= 3.10
- Dependencies: `pandas`, `numpy`, `matplotlib`, `statsmodels`, `arch`, `scipy`, `jupyter` — all pinned in `requirements.txt`

---

## Setup

```bash
git clone https://github.com/Alec-T08/Reproducible-Reaserach-Group-6.git
cd Reproducible-Reaserach-Group-6

python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

---

## How to Run

> ⚠️ Notebooks must run **in order** — Notebook 01 produces `data/combined.csv` which Notebooks 02 and 03 depend on.

```bash
jupyter nbconvert --to notebook --execute src/01_analysis.ipynb --output src/01_analysis.ipynb
jupyter nbconvert --to notebook --execute src/02_cointegration_testing.ipynb --output src/02_cointegration_testing.ipynb
jupyter nbconvert --to notebook --execute src/03_dcc_garch.ipynb --output src/03_dcc_garch.ipynb
```

Or interactively: `jupyter notebook`, then run `01 → 02 → 03`.

**Estimated runtime: 3–8 minutes** (DCC-GARCH optimisation is the slowest step).

---

## Data

| Variable | Source | File |
|----------|--------|------|
| U.S. Dollar Index (DXY) | FRED / Stooq.pl | `data/USD_Index.csv` |
| 10-year Treasury yield | FRED (`DGS10`) | `data/Treasury_Yield.csv` |

Both files are committed to the repository. No downloads or API credentials required.

---

## Repository Structure

```
Reproducible-Reaserach-Group-6/
├── data/                        # Raw and merged data files
├── src/
│   ├── 01_analysis.ipynb        # Run first
│   ├── 02_cointegration_testing.ipynb
│   └── 03_dcc_garch.ipynb
├── output/                      # Pre-rendered figures and tables
├── article/                     # Reference article materials
├── requirements.txt             # Pinned dependencies
├── .gitignore
└── README.md
```

---

## Key Results

**Cointegration (Engle-Granger):**

| Period | p-value | Result |
|--------|---------|--------|
| Full sample (2010–2026) | 0.712 | Not cointegrated |
| Pre-Liberation Day | 0.853 | Not cointegrated |
| **Post-Liberation Day** | **0.027** | **Cointegrated ✓** |

**DCC-GARCH event windows** — conditional correlation declined significantly after April 2, 2025 across all three symmetric windows (p < 0.05), supporting a structural weakening of the dollar-yield relationship consistent with the article's thesis.

Pre-rendered outputs are available in `output/` for inspection without running the code.

---

## Reproducibility

- All paths use `pathlib.Path` (no hardcoded absolute paths)
- Package versions pinned in `requirements.txt`
- Random seed fixed: `np.random.seed(42)` in Notebook 03
- Raw data committed; no external dependencies at runtime

---

## Team

| Name | GitHub |
|------|--------|
| Abdukholik | [@Alec-T08](https://github.com/Alec-T08) |
| Tam Nguyen Bang | [@emma-2304](https://github.com/emma-2304) |
| Elvis Udabor | [@definitely-el](https://github.com/definitely-el) |
| Meifang Wu | [@wmf2241](https://github.com/wmf2241) |

---

## References

Haass, R. N., & Kilcrease, E. (2025). Who profits in a post-American world? *Foreign Affairs*, p. 26.

Engle, R. F., & Granger, C. W. J. (1987). Co-integration and error correction. *Econometrica*, 55(2), 251–276.

Engle, R. F. (2002). Dynamic conditional correlation. *Journal of Business & Economic Statistics*, 20(3), 339–350.

Johansen, S. (1991). Estimation and hypothesis testing of cointegration vectors. *Econometrica*, 59(6), 1551–1580.

---

*Reproducible Research · University of Warsaw · 2025/2026*
