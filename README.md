# Credit Barbell Strategy

This repository contains the final research notebook and output files for a credit barbell allocation strategy with an additional VIX-based risk filter. It is intended to be a clean presentation repository: the final notebook and core deliverables are tracked, while draft notebooks and reference materials are kept out of the GitHub-facing structure.

## Overview

The strategy is built around a barbell framework that combines credit exposure with defensive fixed income exposure. The allocation logic uses macro and credit signals to classify market conditions and then applies a VIX overlay to reduce risk during periods of sharp volatility stress.

In practical terms, the framework is designed to answer three questions:

1. When should the portfolio lean into credit risk?
2. When should it shift toward safer duration-oriented assets?
3. When should an explicit volatility signal force a more defensive posture?

## Strategy Logic

The notebook implements a regime-aware allocation process with the following ideas:

- A barbell structure that balances risk assets and defensive bond exposure
- Credit and macro indicators used as state variables for regime identification
- A VIX-based filter that acts as an additional stress signal
- Backtest validation through cumulative performance, regime transitions, and monthly attribution outputs

The VIX extension is especially important because it adds a fast market-based signal on top of slower macro or spread-based indicators. This helps the framework respond more conservatively during abrupt market dislocations.

## Repository Structure

```text
.
├── credit-barbell-strategy.ipynb
├── data/
├── results/
│   ├── figures/
│   └── reports/
├── README.md
└── .gitignore
```

### Key Files

- `credit-barbell-strategy.ipynb`
  Final notebook containing the full workflow, from data loading and signal construction to backtest evaluation and output generation.
- `data/`
  Placeholder directory for raw or intermediate datasets if local data snapshots are added later.
- `results/figures/`
  Exported charts used to summarize strategy behavior and performance.
- `results/reports/`
  Spreadsheet outputs containing summary statistics, regime-level results, and monthly detail tables.

## Main Outputs

### Backtest Performance

![Backtest Performance](results/figures/backtest_performance.png)

### Regime Timeline

![Regime Timeline](results/figures/regime_timeline.png)

### VIX Signal Comparison

![VIX Signal Comparison](results/figures/signal_comparison_vix.png)

## Report Files

- `results/reports/strategy_VIX_TLT_mix_report.xlsx`
  Summary report for the VIX-enhanced strategy and allocation mix.
- `results/reports/strategy_monthly_details.xlsx`
  Monthly return history and supporting detailed output.
- `results/reports/barbell전략_레짐별 비중과 성과_SAA.xlsx`
  Regime-level portfolio weights and performance breakdown.

## Data Sources

The notebook relies on a combination of market and macroeconomic data. Based on the implementation, the main external inputs are:

- `yfinance` for ETF prices and VIX data
- `fredapi` for macroeconomic and credit-related time series from FRED

Depending on the date range and local setup, the notebook may require internet access when data is refreshed directly from the source APIs.

## Python Dependencies

Recommended core packages:

- `pandas`
- `numpy`
- `matplotlib`
- `yfinance`
- `fredapi`
- `openpyxl`
- `jupyter`

Example installation:

```bash
pip install pandas numpy matplotlib yfinance fredapi openpyxl jupyter
```

## How To Run

1. Create and activate a Python environment.
2. Install the required packages.
3. Add your FRED API key if the notebook requires macro data downloads.
4. Open `credit-barbell-strategy.ipynb`.
5. Run the notebook from top to bottom in sequence.
6. Save or refresh charts and report files under `results/`.

## What Is Included

This repository is intentionally scoped to the final deliverable set:

- one final notebook
- exported figures used for documentation
- report spreadsheets used for result review
- a concise folder structure suitable for GitHub sharing

## What Is Excluded

The following are intentionally not part of the GitHub-facing repository structure:

- draft notebooks
- intermediate experimental files
- reference PDFs
- local environment files

These are kept locally in ignored folders such as `archive/` and `references/`.

## Notes

- This repository is separate from the `regime-detection` project.
- The goal here is not to preserve every research iteration, but to present the final credit barbell strategy in a clean and readable form.
