# Data dictionary

This dictionary describes the supplied workbook. Variable labels and formulas are recorded as they appear in the file; the article is the reference for the research methodology and interpretation.

## Observations and coverage

| Sheet or sample | Observation unit | Retained records |
| --- | --- | --- |
| `RAW DATA` | Company-year emissions record | 32,758 records, reporting years 2018–2023 |
| `CLEANING PHASE I` | Company-year record in the first cleaning snapshot | 32,755 populated company records |
| `FINANCIALS` | Company-year emissions and financial observation | 2,098 populated company records |
| `CLEANING PHASE II` | Earlier/later observation in the retained paired sample | 600 company-year observations for 300 distinct company names |
| `FINAL DATA` | Firm-level elasticity observation | 300 firms across 35 jurisdictions; elapsed periods of 1–5 years |
| `R1 PACE CALCULATION` | Firm-level comparison between two reporting years | 300 firms |
| `R1 PEER COMPARISON` | Firm with observed SIEF reduction | 114 firms |
| Matched 2018–2022 sensitivity | Emissions-reducing firm with that common reporting window | 35 firms |

Counts exclude headers and blank rows. Company identity here follows the workbook's name fields; no external entity-resolution process was applied during documentation. These are successive or overlapping samples and must not be added together.

## Source and financial variables

| Variable | Meaning and storage |
| --- | --- |
| `#` / `Firm ID` | Row or firm identifier within the relevant sheet. Do not assume raw-data row numbers are persistent company identifiers. |
| `Company Name` / `Company` | Company name as recorded in the workbook. |
| `Reporting Year` | Calendar year of the recorded observation. |
| `Jurisdiction` | Jurisdiction label provided in the source sheet. |
| `Sector` | Sector label provided in the source sheet. `Information Not Available` is a missing-information label. |
| `Total Scope 1 GHG Emissions` | Scope 1 emissions, in tonnes of CO₂ equivalent (tCO₂e). Many cells contain text with a unit suffix. |
| `Total Scope 2 Location-based GHG Emissions` | Location-based Scope 2 emissions, in tCO₂e. Kept separately from market-based Scope 2. |
| `Total Scope 2 market-based GHG Emissions` | Market-based Scope 2 emissions, in tCO₂e. This is the Scope 2 field used in the inspected SIEF formulas. |
| `Total Scope 3 GHG Emissions` | Scope 3 emissions, in tCO₂e. |
| `Scope Integrated Emissions Footprint / SIEF` | The inspected workbook formulas sum Scope 1 + market-based Scope 2 + Scope 3. Location-based Scope 2 is not also added. The financial and quadrant sheets store the result as text with a `tCO₂e` suffix; the pace-calculation sheet extracts numeric values. |
| `ROIC` | Return on invested capital. Stored as a fraction in `FINANCIALS` and the earlier/later ROIC columns of `R1 PACE CALCULATION`: `0.155` means 15.5%. |
| `Period (Years)` / `Years` | Elapsed years between the retained earlier and later reporting observations. In `CLEANING PHASE II`, column C bears the label `Period (Years)` but holds reporting-year values; column G computes elapsed years. |

## Derived measures

Let `E₀` and `E₁` denote earlier and later SIEF, `r₀` and `r₁` denote earlier and later ROIC expressed as fractions, and `T` denote elapsed years. The inspected formulas use:

| Measure | Workbook calculation | Units or convention |
| --- | --- | --- |
| Decarbonization–ROIC elasticity | `(r₁ − r₀) / [−(E₁ / E₀ − 1)]` | Original workbook label retained. The numerator is the change in ROIC fractions; the denominator is the proportional SIEF reduction. No division by earlier ROIC appears in the inspected formula. |
| ΔSIEF / Original delta SIEF | `E₁ − E₀` | tCO₂e; negative values represent emissions reduction. |
| ΔROIC in `QUDRANT ANALYSIS` | `r₁ − r₀` | Difference in ROIC fractions. |
| Original delta ROIC | `100 × (r₁ − r₀)` | Percentage points (pp). |
| SIEF change (%) | `100 × (E₁ / E₀ − 1)` | Percentage change over the observed interval. |
| Reduction pace (%/year) | `100 × [1 − (E₁ / E₀)^(1/T)]` | Compounded annual reduction rate; positive when SIEF falls. |
| ROIC change (pp/year) | `100 × (r₁ − r₀) / T` | Annualized ROIC change in percentage points per year. |
| Signed log delta SIEF | `SIGN(ΔSIEF) × LOG10(1 + ABS(ΔSIEF))` | Signed log transformation of the emissions change. |
| Pace relative to peer median | Firm pace minus the observed reducing-peer median pace | Percentage points per year. |

The formula statement above describes the workbook implementation and does not replace the article's methodological definitions.

## Transition quadrants and pace groups

| Quadrant | Workbook condition |
| --- | --- |
| Win–Win | `ΔSIEF < 0` and `ΔROIC ≥ 0` |
| Green Penalty | `ΔSIEF < 0` and `ΔROIC < 0` |
| Brown Win | `ΔSIEF ≥ 0` and `ΔROIC ≥ 0` |
| Lose–Lose | `ΔSIEF ≥ 0` and `ΔROIC < 0` |

The quadrant formula assigns zero changes to the nonnegative side. `R1 PEER COMPARISON` contains reducing firms. Its pace-group formula assigns `Slower` at or below the observed 25th percentile, `Middle` above the 25th percentile and at or below the 75th percentile, and `Faster` above the 75th percentile. The saved cutoffs are approximately 3.2932 and 15.6593 percent per year. `Green Penalty (1/0)` is a binary flag in that reducing-firm subset. Rank formulas use average ranks for ties.

## Import and missing-value guidance

- Preserve company names and jurisdiction labels as text.
- In emissions columns, strip unit suffixes, grouping commas, and nonbreaking spaces deliberately before numeric conversion. Retain the original text when preserving source records.
- Treat blanks, `—`, and `Information Not Available` as missing information. Do not replace them automatically with zero.
- Exclude blank spacer rows in `FINAL DATA`. Its worksheet range extends beyond the 300 populated firm rows.
- Preserve the distinction between ROIC fractions, ROIC percentages, changes in percentage points, and annualized changes.
- Read the README's retained error list before importing intermediate elasticity or permutation-test outputs. Do not turn Excel error strings into numeric values.

Prepared from the supplied workbook on 8 October 2026. No values or formulas were changed during documentation.
