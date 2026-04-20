# src/

This folder contains all source code for the Group 7 Streamlit dashboard.

## Folder Purpose

| File | Purpose |
|---|---|
| `app.py` | Main Streamlit entry point — run this to launch the dashboard |
| `example.py` | Annotated walkthrough of coding conventions (not part of live dashboard) |
| `clean.py` | Data cleaning script — reads raw xlsx from `../data/`, outputs cleaned CSVs |
| `pages/` | (optional) Additional Streamlit pages if multi-page layout is used |
| `utils/` | (optional) Helper modules for chart builders and shared transforms |

## Who works here

**Dhrishita** — Dashboard Developer: `app.py`, `pages/`, `utils/`  
**Desmond** — Data Analyst: `clean.py` (produces cleaned CSVs loaded by the dashboard)

## How to run

```bash
# From the repo root
pip install -r requirements.txt

# Step 1: clean the raw ABS data (run once)
python src/clean.py

# Step 2: launch the dashboard
streamlit run src/app.py
```

## Coding conventions

- Every `pd.read_excel()` or `pd.read_csv()` call must include a comment naming the ABS table number and what it contains.
- Every data transformation (melts, pivots, derived columns) must include a one-line comment explaining *why*, not just what.
- Chart functions should be self-contained — take a DataFrame in, return a Plotly figure out.
- See `example.py` for a working reference of these conventions.
