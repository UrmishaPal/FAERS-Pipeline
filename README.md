# FAERS Q2 2026 Pharmacovigilance Data Analysis

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)](https://pandas.pydata.org/)
[![FDA](https://img.shields.io/badge/Data-FDA%20FAERS-005A9C.svg)](https://www.fda.gov/)
[![Pharmacovigilance](https://img.shields.io/badge/Focus-Pharmacovigilance-2E7D32.svg)]()

## 📌 Project Overview

This project performs an exploratory **pharmacovigilance (PV) analysis of the FDA Adverse Event Reporting System (FAERS) Q2 2026 dataset**.

The workflow demonstrates how publicly available spontaneous adverse-event reporting data can be processed, cleaned, integrated, and analyzed using Python to identify frequently reported drugs, adverse reactions, and drug–reaction reporting patterns.

The project follows a reproducible exploratory pharmacovigilance workflow covering:

**Raw FAERS Data → Data Cleaning → Data Integration → Deduplication → Exploratory Analysis → Drug–Event Analysis → Visualization → Analysis-Ready Outputs**

> **Important:** This project is intended for educational and portfolio purposes. Frequency-based findings represent reporting patterns and should not be interpreted as incidence, risk, or causality.

---

## 🎯 Project Objectives

The primary objectives of this project are to:

- Process raw FAERS quarterly data files.
- Understand the structure of FAERS demographic, drug, and reaction datasets.
- Clean and standardize relevant variables.
- Handle large FAERS files using chunk-based processing.
- Integrate demographic, drug, and adverse-event information.
- Identify frequently reported drugs.
- Identify frequently reported adverse reactions.
- Analyze drug–adverse reaction reporting patterns.
- Examine available demographic characteristics.
- Explore seriousness and outcome information.
- Detect and address duplicate/follow-up case records.
- Generate reproducible pharmacovigilance analysis outputs.
- Create visual summaries of important reporting patterns.

---

## 🏛️ Data Source

**Source:** U.S. Food and Drug Administration (FDA) Adverse Event Reporting System (FAERS)

**Analysis Period:** Q2 2026

**Source:** [FDA FAERS Public Dashboard](https://www.fda.gov/drugs/questions-and-answers-fdas-adverse-event-reporting-system-faers/fda-adverse-event-reporting-system-faers-public-dashboard)

FAERS is a spontaneous reporting system containing adverse-event and medication-error reports submitted to the FDA.

The dataset provides information that can be used for exploratory pharmacovigilance analyses and signal-generating investigations.

---

## 📂 FAERS Files Used

The analysis uses three major FAERS source files:

| File | Description |
|---|---|
| `DEMO` | Patient demographic and administrative case information |
| `DRUG` | Drug/product information associated with reported cases |
| `REAC` | Reported adverse reaction information |

### Key Linking Variables

The analysis uses FAERS identifiers including:

- `primaryid`
- `caseid`

These identifiers allow information from the demographic, drug, and reaction tables to be integrated for analysis.

---

## 🔬 Methodology

### Step 1 — Data Ingestion

The raw FAERS ASCII files are loaded using Python and pandas.

Because FAERS files can be large, **chunk-based processing** is used where appropriate to reduce memory requirements.

```text
Raw FAERS Files
      ↓
DEMO
DRUG
REAC
