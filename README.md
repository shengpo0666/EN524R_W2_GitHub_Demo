# EN524R / CE801V — Environmental Data Research Demo

This repository demonstrates a reproducible environmental data research workflow developed throughout the course.

## Research Question

How does PM2.5 vary over time at Zhongli station, and how is it related to basic meteorological conditions?

---

## Data Sources

### 1. Teaching Sample

Teaching dataset:

`data/sample/zhongli_aq_2025.csv`

Variables in the supplied sample:

- datetime
- station
- PM2.5
- O3
- NO2
- TEMP
- RH
- WS

This small dataset is used for demonstrating data inspection, processing,
visualization, and reproducibility.

### 2. MOENV Air Quality Data

- Provider: Ministry of Environment (MOENV)
- Dataset: AQX_P_432 — Air Quality Index
- Access method: MOENV Open Data API
- Access date: 2026-10-01
- Temporal resolution: Hourly
- Raw snapshot: `data/raw/moenv_AQX_P_432_2026-10-01_sample.json`

For the research workflow, variables should be selected according to the
research question rather than simply using the AQI value.

**Known limitation:**

The snapshot represents data available at the retrieval time and is not a
complete historical dataset.

---

## Research Workflow

The project follows this workflow:

Research Question  
→ Data Source / API  
→ Raw Data  
→ Data Inspection  
→ Data Processing  
→ Analysis-Ready Data  
→ QA/QC  
→ Statistical Analysis  
→ Visualization  
→ Interpretation

Each notebook adds one documented layer to the same research workflow.

---

## W2 — Reproducible Analysis

Notebook:

`notebooks/01_air_quality_demo.ipynb`

Main tasks:

1. Load the teaching dataset.
2. Inspect the data structure.
3. Perform basic QA/QC.
4. Create an exploratory PM2.5 time-series figure.
5. Verify that the notebook can run from top to bottom.
6. Test reproducibility in both JupyterLab and Google Colab.

---

## W3 — Reproducible Data Acquisition

Notebook:

`notebooks/02_data_acquisition.ipynb`

Main tasks:

1. Connect to an environmental data API.
2. Retrieve the selected environmental variables.
3. Inspect the API response structure.
4. Validate shape, columns, missing values, and data types.
5. Save a traceable raw-data snapshot.
6. Document the data source, access date, variables, units, and limitations.

The W3 workflow is:

Retrieve  
→ Inspect  
→ Validate  
→ Save  
→ Document  
→ Commit  
→ Push  
→ Verify

---

## W4 — Data Processing

Notebook:

`notebooks/03_processing.ipynb`

The purpose of W4 is to transform raw observations into an
**analysis-ready table** while keeping all processing decisions traceable.

Main processing steps:

1. Load the raw or teaching data.
2. Inspect shape, columns, data types, and missing values.
3. Parse datetime explicitly.
4. Select variables relevant to the research question.
5. Filter observations when appropriate.
6. Preserve original variables and create derived variables.
7. Aggregate observations using `groupby()` or `resample()` when appropriate.
8. Apply a completeness / valid-count rule for temporal aggregation.
9. Check merge keys, duplicate records, and unmatched observations.
10. Create a processing audit table.
11. Save analysis-ready data to `data/processed/`.

### Processing Audit

The processing notebook should record how the dataset changes during each
major transformation.

Example:

| Step | Rows | Notes |
|---|---:|---|
| Raw load | 168 | Original teaching sample |
| Parse time | 168 | 0 unparsed timestamps |
| Mask negative PM2.5 | 168 | Invalid values → NaN |
| Daily aggregation | 7 | Require sufficient valid hourly observations |

The audit table helps make row loss, exclusions, aggregation, and other
processing decisions visible and traceable.

---

## Repository Structure

```text
EN524R_W2_GitHub_Demo/
├── README.md
├── requirements.txt
├── data/
│   ├── raw/
│   │   └── moenv_AQX_P_432_2026-10-01_sample.json
│   ├── sample/
│   │   └── zhongli_aq_2025.csv
│   └── processed/
├── notebooks/
│   ├── 01_air_quality_demo.ipynb
│   ├── 02_data_acquisition.ipynb
│   └── 03_processing.ipynb
├── figures/
└── src/
