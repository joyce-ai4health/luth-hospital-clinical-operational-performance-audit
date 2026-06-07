# 📁 Project Structure Guide

This document explains the purpose of every folder and file in this repository.
Read this before adding any new file so it lands in the right place.

---

## Repository Layout

```
luth-hospital-clinical-operational-performance-audit/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   └── 02_eda.ipynb
│
├── sql/
│   ├── 01_patient_flow.sql
│   ├── 02_departmental_performance.sql
│   ├── 03_billing_analysis.sql
│   └── 04_los_analysis.sql
│
├── powerbi/
│
├── reports/
│
├── images/
│
├── docs/
│
├── README.md
├── STRUCTURE.md          ← you are here
├── requirements.txt
└── .gitignore
```

---

## Folder & File Reference

### `data/`
Holds all dataset files. Never commit sensitive or personally identifiable data.

| Subfolder | What goes here |
|---|---|
| `raw/` | The original, untouched dataset exactly as downloaded from Kaggle. **Never edit files here.** If something looks wrong, fix it in the cleaning notebook and save the output to `processed/`. |
| `processed/` | Cleaned and transformed datasets produced by the notebooks. The main output file will be `luth_cleaned.csv`. Any intermediate files (e.g. filtered subsets) also live here. |

---

### `notebooks/`
All Jupyter notebooks for Python-based analysis. Notebooks are numbered to show the
order they should be run in.

| File | Purpose |
|---|---|
| `01_data_cleaning.ipynb` | Load the raw dataset, handle missing values, fix data types, standardize formats, and save the cleaned file to `data/processed/`. Run this **first**. |
| `02_eda.ipynb` | Exploratory Data Analysis — charts, statistics, and written findings covering patient demographics, admissions, LOS, department performance, and billing trends. Run this **after** cleaning. |

> **Tip:** Keep markdown cells in every notebook explaining what you are doing and why.
> This turns your notebook into a story, not just code.

---

### `sql/`
SQL query files organized by analysis theme. Each file should have comments at the
top explaining its purpose and comments above each query explaining what it answers.

| File | Covers |
|---|---|
| `01_patient_flow.sql` | Monthly admissions, admission type breakdown, patients by ward |
| `02_departmental_performance.sql` | Department rankings by volume, average LOS per department, doctor workload |
| `03_billing_analysis.sql` | Revenue by department, top billed diagnoses, monthly revenue trends |
| `04_los_analysis.sql` | LOS outliers, LOS by admission type and diagnosis, LOS vs billing cost |

---

### `powerbi/`
Power BI dashboard files (`.pbix`). Each dashboard is saved as a separate file.

| File (planned) | Covers |
|---|---|
| `01_patient_flow_department_performance.pbix` | Patient admissions over time, ward utilisation, departmental workload |
| `02_financial_billing_performance.pbix` | Revenue KPIs, billing by department, LOS vs cost scatter |

> **Note:** `.pbix` files are binary and cannot be previewed on GitHub directly.
> Always export a PDF snapshot of each dashboard and save it in `reports/` so
> reviewers can see the work without opening Power BI.

---

### `reports/`
Written outputs and exported visuals — anything that summarises or presents findings.

| File (planned) | Description |
|---|---|
| `final_report.md` | Full project write-up: background, methodology, findings, and recommendations |
| `executive_summary.md` | One-page plain-English summary for a non-technical audience |
| `dashboard_01_snapshot.pdf` | PDF export of the Patient Flow dashboard |
| `dashboard_02_snapshot.pdf` | PDF export of the Financial Performance dashboard |

---

### `images/`
Screenshots and charts used inside the `README.md` or project documentation.

| What goes here |
|---|
| Dashboard screenshots embedded in the README |
| Key EDA charts worth highlighting at a glance |
| Any other visuals referenced in markdown files |

> **Naming tip:** Use descriptive names like `eda_los_by_department.png` rather
> than `chart1.png` so the purpose is clear without opening the file.

---

### `docs/`
Supporting documents that provide context for the project.

| File (planned) | Description |
|---|---|
| `linkedin_post_draft.md` | Draft of the LinkedIn portfolio post for this project |
| `data_dictionary.md` | Definitions for each column in the dataset (add as you explore the data) |

---

### Root-level Files

| File | Purpose |
|---|---|
| `README.md` | Main project page — visible on GitHub. Should include project overview, tools used, key findings, and links to notebooks and dashboards. Update this last, once the project is complete. |
| `STRUCTURE.md` | This file. Explains the repo layout so any collaborator or reviewer understands where things live. |
| `requirements.txt` | Lists all Python packages needed to run the notebooks. Run `pip install -r requirements.txt` to install them. |
| `.gitignore` | Tells Git which files to ignore (e.g. checkpoint files, system files, large raw data if excluded). Do not delete this. |
| `.gitkeep` | Empty placeholder files used to track empty folders in Git. Delete them once real files are added to that folder. |

---

## Rules to Follow

1. **Never edit files in `data/raw/`** — treat the raw dataset as read-only.
2. **Number notebooks** — if you add a new notebook, continue the numbering (`03_`, `04_`, etc.).
3. **Comment your SQL** — every query should have a comment explaining what business question it answers.
4. **Export dashboard PDFs** — always save a PDF snapshot of Power BI dashboards to `reports/` before closing.
5. **Update the README last** — once the project is done, add screenshots, a findings section, and links.
6. **Delete `.gitkeep` files** once real files have been added to that folder.