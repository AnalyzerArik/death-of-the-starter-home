# Death of the Starter House

**Status: analysis in progress; repository foundation.** This project examines entry-level home-value trends. The title is a research question, not a finding.

## Research question

How have Kansas City's bottom-tier home values changed since 2000 compared with St. Louis, Indianapolis, and the United States, including the period after April 2013?

## Version 1 scope

- **Source:** the Zillow ZHVI All Homes—Bottom Tier, Metro & U.S. dataset already loaded for exploration.
- **Unit:** geography × calendar month; one observation per `RegionID` and `date`.
- **Coverage:** January 2000–August 2026, subject to verified nonmissing coverage in the source snapshot. Use common endpoints for comparisons; label partial years.
- **Comparisons:** Kansas City, MO–KS; St. Louis; Indianapolis; U.S. aggregate. These are descriptive benchmarks, not causal controls. The national series is not another metro.
- **Measures:** nominal bottom-tier ZHVI, April 2013 = 100 index, year-over-year percentage change, and cumulative/annualized change over common periods.

The initial visual exploration suggested a low point and subsequent acceleration around April 2013. The notebook must verify the selected series and observation before reporting that pattern. April 2013 is an exploratory reference date, not an established structural break; January 2013 and January 2014 baselines will provide sensitivity checks.

## Planned outputs

1. Data-quality summary: selected regions, date coverage, missing values, and duplicate-key checks.
2. Monthly value, indexed-growth, and year-over-year charts.
3. Comparison table using common valid endpoints, with baseline sensitivity checks.
4. Short descriptive findings tied to reproducible notebook outputs.

ZHVI estimates home values; it does not measure available listings, construction volume, buyer income, or mortgage payments. This first release cannot establish whether homes are affordable or why values changed. Income, financing, and construction analyses remain later extensions.

## Repository structure

| Path | Purpose |
|---|---|
| `data/raw/` | Local, unchanged Zillow snapshot; excluded from Git |
| `data/processed/` | Generated analysis tables; excluded from Git |
| [data/README.md](data/README.md) | Source recording instructions and required fields |
| `notebooks/` | Existing exploration notebook and subsequent analysis |
| [docs/analysis_plan.md](docs/analysis_plan.md) | Notebook sequence and reporting checks |
| `src/` | Reusable functions extracted when needed |
| `reports/figures/` | Reviewed charts for the final write-up |

## Getting started

Use Python 3.11 or newer:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab
```

On Windows, activate with `.venv\Scripts\Activate.ps1` in PowerShell.

Place the already downloaded data at `data/raw/zillow_bottom_tier_metro.csv`, record its provenance as described in `data/README.md`, and copy the existing notebook into `notebooks/01_zhvi_exploration.ipynb`. Neither the data nor the ongoing notebook is included in this foundation. Run notebooks from the repository root, and preserve original source values and missingness.
