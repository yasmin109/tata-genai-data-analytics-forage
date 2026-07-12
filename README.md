# Geldium Delinquency Prediction — Forage Simulation

End-to-end walkthrough of a delinquency risk analysis for a fictional credit
company ("Geldium"), built for the Forage virtual internship data analyst
simulation. Covers EDA, a predictive modeling plan, a stakeholder report, and
a proposal deck for an agentic AI collections system.

## Project structure

```
geldium-delinquency-project/
├── data/
│   └── Delinquency_prediction_dataset.xlsx   # source dataset (500 customers, 19 fields)
├── scripts/
│   ├── 01_eda_analysis.py                    # pandas EDA: missing data, anomalies, correlations
│   ├── 02_build_eda_report.js                # generates Delinquency_EDA_Report.docx
│   ├── 03_build_modeling_plan.js             # generates Delinquency_Modeling_Plan.docx
│   ├── 04_build_stakeholder_report.js        # generates Geldium_Stakeholder_Report.docx
│   └── 05_build_slide_deck.js                # generates Geldium_Agentic_AI_System.pptx
└── outputs/
    ├── Delinquency_EDA_Report.docx           # Task 1: EDA findings & missing-data treatment plan
    ├── Delinquency_Modeling_Plan.docx        # Task 2: model logic, justification, evaluation strategy
    ├── Geldium_Stakeholder_Report.docx       # Task 3: 1-page business report for Head of Collections
    └── Geldium_Agentic_AI_System.pptx        # Task 4: proposal deck for an agentic AI system
```

## What each task covers

1. **EDA Report** — missing/inconsistent data, key anomalies (out-of-range credit
   utilization, inconsistent employment labels), early risk indicators, and a
   missing-data treatment plan (median imputation with reasoning).
2. **Modeling Plan** — a full pipeline (feature engineering → selection → split →
   class imbalance handling → training → evaluation), a comparison of Logistic
   Regression vs. Gradient Boosted Trees, and a recommendation (Logistic
   Regression, with GBM as a benchmark), plus an evaluation/fairness strategy.
3. **Stakeholder Report** — a 1-page, plain-language summary for a non-technical
   business audience: top 3 risk factors, a SMART recommendation, and an ethics
   section (fairness risks + mitigations).
4. **Slide Deck** — a 6-slide proposal for an agentic AI collections system:
   how it works, autonomous vs. human-in-the-loop responsibilities, responsible
   AI guardrails, and expected business impact.

## Requirements

- Python 3.9+ with `pandas` and `openpyxl` (`pip install pandas openpyxl`)
- Node.js with `docx` and `pptxgenjs` (`npm install docx pptxgenjs`)

## Running it

```bash
# 1. Explore the data (prints findings to console)
cd scripts
python 01_eda_analysis.py

# 2. Generate each Word/PowerPoint deliverable
node 02_build_eda_report.js
node 03_build_modeling_plan.js
node 04_build_stakeholder_report.js
node 05_build_slide_deck.js
```

Each script writes its output directly into `outputs/`.

## Key findings (short version)

- 500 customer accounts, 16% delinquency rate (imbalanced target).
- Individual numeric fields show weak linear correlation with delinquency
  (all < 0.05) — signal is thin and spread across several variables.
- Clearest patterns: **Employment Status**, **Debt-to-Income Ratio**, and
  **Credit Utilization**, each showing threshold-style (not straight-line)
  relationships with delinquency risk.
- Recommended model: **Logistic Regression** — chosen for interpretability,
  regulatory fit, and lower overfitting risk given the small sample size,
  with Gradient Boosted Trees built alongside as a performance benchmark.
