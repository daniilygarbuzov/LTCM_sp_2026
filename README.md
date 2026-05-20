# Low Tide Capital Management — Spring 2026 Project

Trend-following commodity model (Method 1) versus a 60/40 benchmark, with regime and stress analysis.

## Run order

| # | Notebook | Purpose |
|---|----------|---------|
| 1 | [`Notebooks/data_summary.ipynb`](Notebooks/data_summary.ipynb) | EDA on the cleaned trend-asset price file (structure, missing data, return stats, correlation, rolling vol). |
| 2 | [`Notebooks/60_40_construction.ipynb`](Notebooks/60_40_construction.ipynb) | Builds the daily-rebalanced 60/40 NAV (SPXT / LUATTRUU) on the Method 1 calendar, $100M starting NAV. |
| 3 | [`Notebooks/trend_model_method1_backtest_updated.ipynb`](Notebooks/trend_model_method1_backtest_updated.ipynb) | Method 1 commodity-trend backtest (20/63-day SMA signals, 25% AUM per active signal) with trade stats, turnover, and performance exhibits. |
| 4 | [`Notebooks/build_interest_rate_regimes.ipynb`](Notebooks/build_interest_rate_regimes.ipynb) | Six-state yield-curve regime classifier from 2Y/10Y yields (21/200 SMA differentials, dead-zones, 5-day persistence). Writes `data/interest_rate_regimes.xlsx`. |
| 5 | [`Notebooks/trend_vs_60_40_analysis.ipynb`](Notebooks/trend_vs_60_40_analysis.ipynb) | Six-part comparison of trend vs 60/40: performance, correlation, mean-variance blends, drawdowns, equity/bond sleeves, positive stock-bond correlation. |
| 6 | [`Notebooks/trend_vs_60_40_regime_analysis.ipynb`](Notebooks/trend_vs_60_40_regime_analysis.ipynb) | Performance conditional on yield-curve regime, event studies around regime changes, and a long-only 3-asset (Stock, Bond, Commodity-Trend) dynamic MV allocator. |
| 7 | [`Notebooks/trend_vs_60_40_presentation.ipynb`](Notebooks/trend_vs_60_40_presentation.ipynb) | Slide-ready charts and tables. Reads CSVs produced by notebooks 3-6; runs no backtests itself. |

Independent: [`QuantCubeValidation/ReplicatingQuantCube.ipynb`](QuantCubeValidation/ReplicatingQuantCube.ipynb) — replicates the QuantCube CPI nowcast against BLS CPI, SOFR futures, and 5Y breakevens for the 2021 inflation breakout.

## Layout

- `data/` — raw and cleaned input files (Bloomberg/FRED).
- `Notebooks/output/` — CSVs consumed by the analysis and presentation notebooks.
- `Notebooks/output_method1/` — CSVs and PNGs produced by the Method 1 backtest.
- `Notebooks/trend_analysis/` — Python package with shared plotting and table helpers used by notebooks 5-7.

## Dependencies

Python 3.10+ with `numpy`, `pandas`, `matplotlib`, `openpyxl`, `pandas_datareader` (for the QuantCube notebook), and Jupyter.
