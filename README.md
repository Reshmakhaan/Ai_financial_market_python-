# 📈 AI Financial Market Analysis — Realistic Synthetic Dataset

![cover](https://images.unsplash.com/photo-1559526324-593bc073d938?auto=format\&fit=crop\&w=1350\&q=80)

> **Project:** Realistic Synthetic — AI Financial Market Data for Gemini (Google), ChatGPT (OpenAI), Llama (Meta)

---

## 🔎 Project Overview

This repository contains a complete data analysis project that explores a synthetic daily financial dataset (2015-01-01 to 2024-12-31) for companies that developed prominent AI products: **OpenAI (GPT)**, **Google (Gemini)**, and **Meta (Llama)**. The goal is to extract actionable financial and event-driven insights that would be useful for finance professionals, quant analysts, and data-driven product/strategy teams.

Key business problems addressed:

* How much did companies spend on R&D across time, and how did that relate to revenue?
* How did product launches and major events affect stock impact (daily index changes)?
* Which events caused the highest market response?
* What is the trajectory of AI revenue growth per company?
* How do financial metrics correlate (R&D vs Revenue vs Stock Impact)?


---

## 📁 Repository Structure

```
├── data/                      # raw and processed CSV files
│   ├── ai_financial_market_daily_realistic_synthetic.csv
│   └── processed/             # cleaned subsets and aggregated CSVs
├── notebooks/                 # exploratory and analysis notebooks
│   ├── 01_data_cleaning.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_event_impact_analysis.ipynb
│   └── 04_final_report.ipynb

├── outputs/                   # charts, tables, and figures for presentation
├── README.md                  # this file
└── presentation/              # slides for interviews (PDF / pptx)
```

---

## 🧾 Dataset Summary

* **Coverage:** 2015-01-01 to 2024-12-31 (daily granularity)
* **Companies:** OpenAI, Google, Meta
* **Core variables (sample):**

  * `date` — day
  * `company` — OpenAI / Google / Meta
  * `r_and_d_spend` — daily R&D expense (synthetic)
  * `revenue` — daily revenue (synthetic)
  * `stock_index` — synthetic index or stock price proxy
  * `stock_impact` — derived measure: daily percent change vs previous close
  * `event` — text label if a product/event happened that day (launch, update, earnings, etc.)

> Note: dataset is synthetic but realistic; documented assumptions and event annotations are included in `/data/README_data_dictionary.md`.

---

## 🛠️ Tech Stack

* Python (pandas, numpy, scikit-learn, statsmodels)
* Jupyter Notebooks for exploration and narrative
* Matplotlib / Plotly for visualizations (static and interactive)
* seaborn for quick EDA
* Git & GitHub for version control and presentation

---


### 1) R&D Spending — Cumulative & Yearly

* Aggregate R&D spend per company (yearly totals, CAGR).
* Visuals: stacked area chart (2015–2024) + bar chart showing year-by-year spend.
* Recruiter take-away: show how you convert daily noise into strategic yearly insights and calculate meaningful KPIs (CAGR, % of revenue spent on R&D).

### 2) Revenue Earned by Companies

* Yearly revenue totals and YoY growth rates for each company.
* Visuals: grouped bar charts, growth rate lines, waterfall for year-to-year changes.

### 3) Date-wise Impact on the Stock

* Compute daily `stock_impact = (stock_index - stock_index.shift(1)) / stock_index.shift(1)`.
* Plot time-series with event markers (launches, earnings, major press).
* Highlight abnormal returns using z-score or rolling volatility.

### 4) Events when Maximum Stock Impact was Observed

* Rank events by absolute stock impact across companies.
* Provide event-level case studies (e.g., product launch — pre vs post 30-day returns).
* Visuals: top 10 event cards with mini time-series and impact metric.

### 5) AI Revenue Growth of the Companies

* Decompose revenue into AI-related (if annotated) vs non-AI (if available).
* Fit simple growth models and compute projected AI revenue share.

### 6) Correlation between Key Columns

* Correlation matrix (Pearson + Spearman for robustness).
* Pairplots for relationships: R&D vs Revenue, R&D vs Stock Impact, Revenue vs Stock Impact.
* Discuss multicollinearity implications for regression.

### 7) Expenditure vs Revenue Year-by-Year

* Scatter + regression lines per year and by company.
* KPI: R&D-to-Revenue ratio and its trend.

### 8) Event Impact Analysis

* Event study window analysis ([-30, +30] trading days) computing cumulative abnormal returns (CAR).
* Hypothesis testing (t-test or bootstrap) to see whether event windows produced statistically significant returns.

### 9) Change in Index w.r.t Year & Company

* Annualized volatility, average returns, max drawdown per year and company.
* Heatmap for quick visual comparison.

---

## 📊 Key Visual Deliverables (include in `outputs/`)

* `fig_r_and_d_trends.png` — stacked area showing cumulative R&D
* `fig_revenue_growth.png` — multi-company revenue growth
* `fig_event_timeline.png` — timeline annotated with major events and impacts
* `fig_top_events_impact.png` — bar chart of events ranked by impact
* `fig_corr_matrix.png` — annotated correlation heatmap
* `fig_event_study_companyX.png` — example CAR plot for top events


---

## ✅ Reproducibility & How to Run

1. Clone the repo

```bash
git clone <your-repo-url>
cd ai-financial-market-analysis
```

2. Create environment and install packages

```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

3. Run the notebooks in order (01 → 04) or execute `src/data_pipeline.py` to regenerate processed datasets.

---

## 🎯 Top Insights (example highlights to include in portfolio)

* **R&D intensity:** Company A spent an average of X% of revenue on R&D (2019–2024), and increases in R&D spend preceded revenue accelerations by ~12 months.
* **Event sensitivity:** Product launches produced median 5-day CAR of +Y% (statistically significant at p < 0.05) for the launching company.
* **Correlation:** R&D and revenue show a moderate positive correlation (Pearson r ≈ 0.46), while R&D and same-day stock impact are weakly correlated.
* **Top-impact events:** A ranked list of the top 10 events (with short descriptions) showing market reactions.

*(Numbers above are placeholders — use computed values from `notebooks/04_final_report.ipynb`.)*

---
---


## 🔐 Ethics & Data Notes

* The dataset is synthetic and constructed to mimic real-world patterns — all modeling and claims in the repository are restricted to exploratory analysis and demonstration purposes only.
* Documented assumptions and the noise model used to synthesize daily values are included in `/data/README_data_dictionary.md`.

---


---

<p align="center">Made with ❤️ • Data Analysis • Python • Jupyter</p>
