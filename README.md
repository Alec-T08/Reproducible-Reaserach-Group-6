# Replicating "Who Profits in a Post-American World?" — Group 6

## Overview

This project attempts to replicate and extend the empirical analysis discussed in the *Foreign Affairs* article **"Who Profits in a Post-American World?"**, which examines the economic consequences of Trump-era tariff policies and the unusual divergence between the **U.S. Dollar Index (DXY)** and **10-year U.S. Treasury yields** observed in 2025.

Under typical market conditions, the dollar and Treasury yields move together — both rise during risk-off episodes as investors flock to U.S. assets. The article argues that the tariff shock broke this relationship, raising yields while simultaneously weakening the dollar — a pattern more reminiscent of emerging market stress than a reserve currency country.

---

## Research Question

> *Did Trump-era tariff announcements cause a structural break in the historical co-movement between the U.S. Dollar Index (DXY) and 10-year U.S. Treasury yields?*

---

## Methodology

We follow the article's framework and apply the following econometric tools:

- **Descriptive analysis** of DXY and 10-year Treasury yield time series around key tariff announcement dates
- **Correlation analysis** to measure the breakdown in co-movement
- **Cointegration testing** (Engle-Granger) to assess the long-run relationship
- **DCC-GARCH** or **Markov-switching models** to capture regime changes in the correlation structure
- **Event study** around major tariff announcement dates

---

## Data Sources

| Variable | Source |
|---|---|
| U.S. Dollar Index (DXY) | FRED / Stooq.pl |
| 10-year U.S. Treasury yield | FRED (series: DGS10) |
| Tariff announcement dates | Policy tracker / news sources |
| Equity market indices | Stooq.pl / Yahoo Finance |

---

## Repository Structure

```
Reproducible-Reaserach-Group-6/
│
├── data/               # Raw and cleaned data files
├── scripts/            # Analysis scripts (Python / R)
├── notebooks/          # Jupyter / Quarto notebooks
├── output/             # Figures, tables, results
├── report/             # Final rendered report
└── README.md
```

---

## Team — Group 6

| Name | GitHub |
|---|---|
| Abdukholik | @Alec-T08 |
| Tam Nguyen Bang | emma-2304 |
| *(teammate 3)* | *(GitHub username)* |
| *(teammate 4)* | *(GitHub username)* |

---

## Reference

> *"Who Profits in a Post-American World?"*, Foreign Affairs, 2025.

---

## Course

**Reproducible Research** — University of Warsaw, Master's Programme, Semester IV, 2025/2026
