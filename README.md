# Carbon Payoff

Research data and Excel analyses accompanying:

**When Does Decarbonization Pay? Mapping Elasticity and Climate Information Capabilities in the Corporate Transition**

**Author:** Samer Abaddi  
**Journal:** *Carbon Management*  
**Status:** Accepted for publication on 8 October 2026  
**Article DOI:** [10.1080/17583004.2026.2746370](https://doi.org/10.1080/17583004.2026.2746370)

## Overview

This repository accompanies the article and provides the supplied research workbook, including corporate greenhouse gas emissions, return on invested capital (ROIC), decarbonization–ROIC elasticity calculations, transition quadrants, and decarbonization-pace analyses. Consult the article for the study design, sample-selection rationale, and interpretation of the results.

The workbook contains **17 worksheets**. Its raw-data sheet holds **32,758 company-year records covering 2018–2023**. The final dataset contains **300 firms across 35 jurisdictions**, with one retained elasticity observation per firm. The pace analyses include a subset of **114 emissions-reducing firms**. These counts describe different stages of the workbook and should not be treated as interchangeable samples.

## Files

| File | Contents |
| --- | --- |
| [`data/data_and_analysis.xlsx`](data/data_and_analysis.xlsx) | Original Excel workbook, renamed for a stable repository path. Its contents and formulas are preserved. |
| [`CITATION.cff`](CITATION.cff) | Machine-readable dataset metadata and the associated article as the preferred citation. |
| [`docs/DATA_DICTIONARY.md`](docs/DATA_DICTIONARY.md) | Variable definitions, units, calculation conventions, and missing-value guidance. |
| [`docs/ABOUT_THIS_FILE.txt`](docs/ABOUT_THIS_FILE.txt) | Suggested text for the workbook's first worksheet, `ABOUT THIS FILE`. |
| [`checksums.sha256`](checksums.sha256) | SHA-256 checksum of the deposited workbook. |

## Workbook guide

Worksheet names below match the supplied file, including the spelling of `QUDRANT ANALYSIS`.

| Worksheet | Contents |
| --- | --- |
| `ABOUT THIS FILE` | Empty introductory sheet in the supplied workbook. Suggested introductory text is provided separately. |
| `RAW DATA` | Company-year emissions records, company names, reporting years, jurisdictions, and sectors. |
| `CLEANING PHASE I` | First retained data-cleaning snapshot. |
| `FINANCIALS` | Emissions records combined with ROIC and the Scope Integrated Emissions Footprint (SIEF). |
| `ELASTICITY CALCULATION` | Decarbonization–ROIC elasticity calculations from earlier and later observations. |
| `CLEANING PHASE II` | Further sample preparation, paired observations, and elapsed-year calculations. |
| `FINAL DATA` | Final 300-firm dataset, including period, jurisdiction, sector, and elasticity. |
| `DESCRIPTIVES` | Summary statistics and counts of positive and negative elasticity values. |
| `PIVOT ANALYSIS` | Pivot summaries, including average elasticity by jurisdiction. |
| `QUDRANT ANALYSIS` | Changes in SIEF and ROIC, transition-quadrant classifications, and category frequencies. |
| `COMPANY SCATTER` | Company-level plot data for emissions and ROIC changes. |
| `R1 PACE CALCULATION` | Firm-level annualized emissions-reduction pace, ROIC changes, and rankings. |
| `R1 PACE TABLE` | Summaries by pace group and supporting interval calculations. |
| `R1 PEER COMPARISON` | Pace groups and rankings for 114 observed emissions-reducing firms. |
| `R1 STATISTICAL TESTS` | Association tests, group comparisons, and sensitivity statistics. See the retained limitations below. |
| `R1 PACE FIGURE` | Plot data for annualized pace and annualized ROIC changes. |
| `R1 MATCHED WINDOW` | Sensitivity data, including the common 2018–2022 window and unannualized ROIC changes. |

## Using the workbook

1. Download `data/data_and_analysis.xlsx` and open it in a recent version of Microsoft Excel. Some formulas use functions such as `TEXTBEFORE`, `RANK.AVG`, and `QUARTILE.INC`; support may vary in other spreadsheet applications.
2. Start with `FINAL DATA` for the retained firm-level elasticity dataset, or `R1 PACE CALCULATION` for the 300-firm pace analysis. Use `R1 PEER COMPARISON` for the 114-firm emissions-reducing subset.
3. Consult the data dictionary before converting units or importing the sheets. Several emissions columns contain text with unit suffixes, and `FINAL DATA` contains blank spacer rows.
4. Treat blanks, the em dash (`—`), and `Information Not Available` as missing information rather than numerical zero. Keep the two Scope 2 reporting bases separate.

## Citation

When using these materials, cite the associated article and identify the repository version or commit used. Until the journal supplies final publication metadata, use:

> Abaddi, S. (in press). When does decarbonization pay? Mapping elasticity and climate information capabilities in the corporate transition. *Carbon Management*. https://doi.org/10.1080/17583004.2026.2746370

`CITATION.cff` records the article as the preferred citation and identifies 2026 as the acceptance year. Volume, issue, page range, and online publication date are omitted because they have not been supplied. Update the citation when the publisher's final bibliographic record becomes available.

**The DOI above identifies the article. A separate DOI has not been assigned to this dataset.**

## Provenance and reuse

The deposited workbook was supplied by Samer Abaddi as the data and analysis associated with the accepted manuscript. Original upload name: `DATA & ANALYSIS(1).xlsx`. The repository copy has been renamed without changing its bytes.

A standalone statement of the original emissions and financial-data providers, retrieval dates, selection rules, and reuse terms did not accompany the supplied file. Consult the article and obtain those source details from the author before extending the dataset. A reuse license has not been specified for this deposit.

## Contact

**Samer Abaddi** — [GitHub profile](https://github.com/SamerAbaddi)

For questions about the data or methods, contact the author. Once the repository is published, issues can be used to report file or documentation problems.
