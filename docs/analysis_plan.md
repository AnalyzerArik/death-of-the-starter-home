# Initial notebook plan

Continue the existing exploration in `notebooks/01_zhvi_exploration.ipynb`; do not recreate completed work.

1. **Load and audit.** Read the unchanged local snapshot; verify series metadata; identify Kansas City, St. Louis, Indianapolis, and U.S. rows by labels and types, retaining their IDs. Display geography selection, coverage, missingness, and duplicate-key checks.
2. **Reshape.** Convert month columns to `(RegionID, date, bottom_tier_zhvi)` observations with retained geography metadata. Preserve missingness and check monthly continuity.
3. **Describe.** Plot nominal monthly values, April 2013 = 100 indices, and year-over-year changes. State geography, source snapshot, time window, and units on every output.
4. **Compare.** Produce a common-endpoint table with start/end values, cumulative change, annualized change, and coverage. Repeat indexed comparisons using January 2013 and January 2014. Report unavailable baselines explicitly.
5. **Verify the exploratory pattern.** Check the Kansas City series and the relevant window before describing the apparent April 2013 trough. Distinguish a visual increase in slope from a formally tested change in growth. Do not backfill the approximately $60,324 observation from memory.
6. **Report.** Export reviewed figures to `reports/figures/` and analysis tables to `data/processed/`. Write only findings supported by saved, reproducible outputs and explicit comparison periods.

Before publishing the analysis, restart the notebook kernel and run all cells from the documented inputs. Confirm output keys, missing-value handling, denominator dates, and relative file paths. Record the tested dependency versions then.

## Interpretation limits

- Values and percentage changes are nominal; they are not inflation-adjusted purchasing power.
- Bottom-tier home values are an entry-level price proxy, not a count of starter homes for sale.
- Relative price growth does not establish housing affordability without income and financing inputs.
- St. Louis, Indianapolis, and the U.S. series are benchmarks, not matched controls.
- An exploratory baseline selected after viewing a chart cannot establish a causal break or explain its cause.
- Zillow revisions and differing coverage may change results; retain snapshot provenance.
