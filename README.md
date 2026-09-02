 [README.md](https://github.com/user-attachments/files/31744150/README.2.md)
# FAERS Q2 2026 Pharmacovigilance Data Analysis

## Project Overview
This project analyzes data from the FDA Adverse Event Reporting System (FAERS) for Q2 2026 to explore reported drug-related adverse events and identify frequently reported drug–reaction associations. The workflow reflects a standard exploratory pharmacovigilance (PV) approach to spontaneous adverse event reporting data, including data cleaning, integration, and signal-generating summary statistics.

## Objectives
- Clean and structure raw FAERS data files
- Integrate demographic, drug, and adverse-event data
- Identify frequently reported drugs and adverse reactions
- Analyze drug–adverse reaction reporting patterns
- Summarize available demographic and seriousness/outcome information
- Generate reproducible, analysis-ready outputs for downstream pharmacovigilance review

## Dataset
**Source:** FDA Adverse Event Reporting System (FAERS) Quarterly Data Extract, publicly available via the [FDA FAERS Public Dashboard](https://www.fda.gov/drugs/questions-and-answers-fdas-adverse-event-reporting-system-faers/fda-adverse-event-reporting-system-faers-public-dashboard)
**Data period:** Q2 2026
**Files used:**
- `DEMO` — patient demographic and administrative case data
- `DRUG` — drug/product information per case
- `REAC` — reported adverse reaction terms per case

*Note: FAERS source files may contain duplicate `caseid` entries across submissions and quarters. Deduplication logic (retaining the most recent `fda_dt`/highest `caseversion` per `caseid`) [was applied / is planned] to reduce double-counting — see Limitations.*

## Methodology
1. Loaded FAERS source files (ASCII, pipe-delimited) using Python and pandas.
2. Processed large files using chunk-based loading to manage memory usage.
3. Selected relevant variables from the demographic, drug, and reaction datasets.
4. Merged records across datasets using `primaryid` and `caseid` as linking keys.
5. Deduplicated cases to mitigate known FAERS duplicate-reporting issues.
6. Explored the most frequently reported drugs and adverse reactions.
7. Generated drug–reaction frequency tables to surface potential reporting associations.
8. Performed demographic and seriousness/outcome exploration (age, sex, outcome codes).
9. Created visualizations of key reporting patterns.
10. Exported analysis-ready CSV outputs for further review.

## Key Outputs
| File | Description |
|---|---|
| `FAERS_Q2_2026_merged_dataset.csv` | Cleaned, merged demographic + drug + reaction dataset |
| `FAERS_top_drugs.csv` | Most frequently reported drugs |
| `FAERS_top_adverse_reactions.csv` | Most frequently reported adverse reaction terms |
| `FAERS_top_drug_reaction_pairs.csv` | Most frequently reported drug–reaction combinations |

## Tools & Technologies
- Python
- Pandas / NumPy
- Matplotlib
- Google Colab
- GitHub

## Limitations
- **No denominator data:** FAERS contains only reported events, not total drug utilization, so reporting counts cannot be converted into incidence or reporting rates.
- **Reporting bias:** Spontaneous reporting is subject to stimulated reporting, underreporting, and media/publicity effects, which can distort apparent frequency.
- **Data quality:** Raw `drugname` fields are frequently inconsistent (brand vs. generic names, misspellings, combination products) and were not mapped to a standardized terminology (e.g., MedDRA Preferred Terms) in this iteration.
- **Duplicate cases:** FAERS is known to contain duplicate and follow-up case submissions; deduplication was handled at the `caseid` level but may not capture all duplicates.

## Important Interpretation Note
FAERS is a spontaneous reporting database. Reporting frequency should not be interpreted as incidence, prevalence, or proof of causality between a drug and an adverse event. Findings in this project represent **reported associations only** and require further clinical and pharmacovigilance assessment before any causal or risk conclusions are drawn.

## Skills Demonstrated
- Pharmacovigilance data analysis
- FAERS data processing and structure
- Data cleaning, deduplication, and validation
- Large dataset handling (chunked processing)
- Multi-table data integration
- Exploratory data analysis
- Drug–event association analysis
- Data visualization
- Python / pandas
- Reproducible analytical workflow
