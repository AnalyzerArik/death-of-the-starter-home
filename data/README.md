# Data contract

The initial source is the already loaded Zillow **ZHVI All Homes—Bottom Tier, Metro & U.S.** snapshot. Its recorded notebook path is `raw/zillow/2026-10-01/zillow_bottom_tier_metro.csv`; the packaged notebook also accepts `raw/zillow_bottom_tier_metro.csv`. Confirm the actual download's series identity, housing type, adjustment settings, and coverage before interpreting it as bottom-tier values. Do not substitute a typical-value or single-family-only series without documenting the change.

Record the original filename, source URL, retrieval date (if known), adjustment settings, minimum/maximum month, and SHA-256 hash in `source_metadata.csv`. Leave unknown fields blank until verified; never infer a retrieval date from the last observation or a folder date. The manifest now records only supported notebook/context information; missing download identity and checksums remain blank. Its source URL is the selection page, not the exact CSV URL. See [source provenance](../docs/source_provenance.md) for evidence levels and missing inputs. Preserve source revisions as separate snapshots.

## Required fields

| Field | Role |
|---|---|
| `RegionID` | Zillow geography identifier; retain source value |
| `RegionName` | Geography label used to confirm the selected rows |
| `RegionType` | Distinguishes metro and national observations |
| `StateName` | Source state label; may be absent for the U.S. aggregate |
| `SizeRank` | Source metadata; not an affordability ranking |
| Monthly `YYYY-MM-DD` columns | Values to reshape into long format |
| `date` | Parsed calendar month from the wide date columns |
| `bottom_tier_zhvi` | Numeric nominal value; retain missing observations |
| `index_2013_04` | `100 * value / geography's April 2013 value` |
| `yoy_pct` | `100 * (value / value exactly 12 months earlier - 1)` |

The long-form primary key is `(RegionID, date)`. Verify uniqueness and one observation per calendar month before calculating lagged measures. A missing or nonpositive baseline produces an unavailable index, not a zero. Missing either year-over-year endpoint produces an unavailable growth rate.

Confirm exactly one source row for each selected geography: Kansas City, MO–KS; St. Louis; Indianapolis; United States. Record the actual source names and IDs rather than guessing IDs or treating the first row as national.

Use the intersection of available endpoint dates for comparisons, report gaps within each series, and keep national and metro labels distinct. Derive cumulative change as `100 * (end / start - 1)` and annualized change as `100 * ((end / start) ** (12 / elapsed_months) - 1)` for positive values and a positive elapsed interval.

Raw, interim, and processed data files are ignored by Git. Commit documented outputs only after review. Archived appendix inputs (ACS and FRED) do not extend the version 1 data contract; their observed use is recorded separately in the provenance document.
