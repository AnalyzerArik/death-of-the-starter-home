# Source provenance and verification boundaries

Recorded during notebook publication on October 5, 2026. The repository baseline was `4af3877541696033abbad4ec81a2cb0e4c211e25` (October 3, 2026). This document preserves that version 1 scope; it does not introduce new research questions.

## Imported workbook

- Input: `01_data_exploration.ipynb`, saved October 5, 2026.
- Input SHA-256: `e6bcd401ffc0bdaebc6bb26a19c162d57d15ad7dd8ce696d0d42560fda7cbde8`.
- Repository copy: `notebooks/01_zhvi_exploration.ipynb`.
- Recorded runtime: Python 3.12.4 and pandas 2.2.2. Other dependency versions are not recorded.
- Packaging changes: added evidence/status notes, made project-root detection portable, retained calculations and saved numeric outputs, removed the local username/path printout, and removed bundled Plotly JavaScript plus duplicate chart HTML. Structured Plotly chart data, PNG previews, and tables remain.
- Original income/payment code is retained as an archived exploratory appendix with execution disabled by default. It is excluded from version 1 findings.

## Zillow — version 1 source

| Field | Evidence available |
|---|---|
| Recorded selection | ZHVI All Homes—Bottom Tier, Metro & U.S., from the project setup; raw settings not independently checked |
| Selection page | [Zillow Research data](https://www.zillow.com/research/data/); this is not the exact CSV download URL |
| Local filename | `zillow_bottom_tier_metro.csv` |
| Recorded input path | `data/raw/zillow/2026-10-01/zillow_bottom_tier_metro.csv` |
| Original filename / exact download URL | Unknown |
| Retrieval time | Unknown; the dated path alone does not establish it |
| Seasonal adjustment / smoothing settings | Unknown |
| CSV SHA-256 | Unknown; no raw bytes were available for publication review |
| Saved loaded dimensions | 892 rows × 325 columns, from the original notebook output |
| Saved month coverage | January 2000–August 2026; 320 monthly columns represented in the Kansas City chart |
| Saved Kansas City identity | `RegionID=394735`, `RegionName=Kansas City, MO`, `RegionType=msa`, `StateName=MO` |
| Saved national identity | First displayed source row has `RegionID=102001`, `United States`, `country`; national selection and coverage have not been audited |
| Peer identities | St. Louis / Indianapolis rows and IDs have not been verified |

The intended Kansas City benchmark is the metro, not city limits. Preserve the actual source label and ID. Confirm geographic coverage from source metadata before joining to other geography definitions.

The manifest in `data/source_metadata.csv` records supported fields and leaves unknown values blank. Coverage there comes from saved outputs. Never hash the notebook and present that value as the raw CSV hash. A fresh download can revise historical values and must be recorded as a distinct snapshot.

## Verification performed during publication

The nominal Plotly trace contains 320 Kansas City date/value pairs. The review checked monthly continuity, missingness, duplicate months, the 2011–2014 minimum, the April 2013 value, the entire saved YoY series, its maximum, and the 2019 / 2024 annual averages and percentage change against those pairs. All checks passed. This is an internal-consistency check using data embedded in the workbook, not an independent source replication.

No source-backed full run was performed. Original CSV provenance, all comparison rows, common valid endpoints, indexed comparisons, and baseline sensitivity checks remain pending. Nominal home-value growth is descriptive; it establishes neither affordability nor the causes of market changes.

## Archived appendix inputs — outside version 1 findings

These references document code already present in the workbook. They do not authorize new analysis scope or verify the saved appendix results.

| Input | Recorded code and local output | Gaps |
|---|---|---|
| Census ACS 1-year, 2019 and 2024 | `https://api.census.gov/data/2019/acs/acs1` and `https://api.census.gov/data/2024/acs/acs1`; requested `NAME,B19013_001E,B19013_001M` for metro/micro area `28140`; saved `data/raw/census/<run-date>/acs1_<year>_kc_income.json` | Original JSON responses, retrieval dates, hashes, and geography-definition comparability not verified |
| FRED `MORTGAGE30US` | Code URL: `https://fred.stlouisfed.org/graph/fredgraph.csv?id=MORTGAGE30US`; saved `data/raw/fred/<run-date>/MORTGAGE30US.csv`; weekly observations averaged by calendar month | Original CSV, retrieval date, hash, and source-methodology changes not checked |

The Census key is requested with `getpass`; no key value is embedded in the published source. Raw and interim inputs stay outside Git. Enabling the appendix performs live requests; a later response is not proof of the historical run. Its model decomposition allocates a modeled payment difference under fixed assumptions and is not a causal estimate of housing-market drivers.

## Requirements for source-verified release results

1. Recover the exact original Zillow snapshot and record its metadata and SHA-256; keep unknown settings explicit until resolved.
2. Restart and run the version 1 notebook using that documented snapshot; record tested dependencies.
3. Complete all four geography audits, common-period comparisons, and baseline sensitivity checks in the existing analysis plan.
4. Review outputs and cite their exact geography, units, periods, and verification limits before writing final findings.
