# EN524R / CE801V — Week 2 GitHub Demo

## Research Question
How does PM2.5 vary over time at Zhongli station, and how is it related to basic meteorological conditions?

## Data
Teaching dataset: `data/sample/zhongli_aq_2025.csv`

Columns in the supplied sample:
- datetime
- station
- PM2.5
- O3
- NO2
- TEMP
- RH
- WS

## Workflow
1. Open `notebooks/01_air_quality_demo.ipynb`.
2. Run all cells from top to bottom.
3. Inspect the data and document one QA/QC decision.
4. Create an exploratory PM2.5 time-series figure.
5. Verify the notebook runs in both JupyterLab and Google Colab.

## Environment
Python 3 with:
- pandas
- matplotlib

Install dependencies with:

```bash
pip install -r requirements.txt
```

## Reproducibility Note
Large/raw datasets should not be committed to the repository. Use `data/sample/` for a small reproducible teaching sample and document the original data source in this README.

## AI Assistance
If AI tools are used, document what they assisted with and how the output was verified.

## W2 Tutorial Test
This line was added locally to demonstrate the Git commit and push workflow.
