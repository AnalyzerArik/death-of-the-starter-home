# Initial notebook plan

Continue the existing exploration in `notebooks/01_zhvi_exploration.ipynb`; do not recreate completed work.

## Publication status — October 5, 2026

The local `01_data_exploration.ipynb` has been packaged under the planned repository name. Saved Kansas City outputs are preserved. File paths now support the repository root or `notebooks/`; bundled Plotly JavaScript and duplicate chart HTML were removed while structured chart data and PNG previews were retained. The original input notebook is identified by SHA-256 in [source_provenance.md](source_provenance.md).

| Work | Current evidence / status |
|---|---|
| Kansas City row selection | Saved output identifies `394735`, `Kansas City, MO`, `msa`, `MO`; code asserts exactly one matching row |
| Kansas City monthly reshape and coverage | Saved chart contains 320 consecutive months, January 2000–August 2026; review confirmed no missing values or duplicate months in that embedded series |
| Nominal and YoY charts | Preserved; all saved YoY values checked against 12-month calculations from the embedded nominal series |
| April 2013 observation | About USD 60,324 in the saved series; the minimum in the 2011–2014 window is March 2012, about USD 59,537 |
| 2019 / 2024 annual averages | Saved series reproduces nominal averages of about USD 113,478 / 185,359 and 63.3% change; both years have 12 months |
| Original CSV identity, settings, hash, and clean rerun | Pending; raw source bytes were not available during publication |
| St. Louis, Indianapolis, U.S. row audits and four-series quality summary | Pending; not present in the completed local notebook |
| April 2013 index, common-endpoint comparison, annualized growth | Pending |
| January 2013 / January 2014 baseline sensitivity | Pending |
| Reviewed version 1 figure exports and final findings | Pending |

**Verified here means internally checked against saved notebook chart data only.** It does not mean independently source-verified. Do not promote these observations into final release findings until source provenance and the clean rerun are complete. The initial visual suggestion of acceleration remains exploratory; no structural-break or causal test was performed.

The original workbook's ACS / FRED payment experiments remain in an **archived exploratory appendix**, excluded from version 1 findings and disabled by default. They are preserved work, not additions to the approved question. Appendix results were not independently verified during this publication.

## Remaining sequence within the confirmed scope

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
