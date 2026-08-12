# 🎓 College Majors 2026: Analysis & Insights

> **Can your college major predict your financial future — and how much does AI reshape that equation?**  
> This project explores 228,000 U.S. degree programs to find out.

---

## 📌 Overview

This end-to-end data analysis project examines the **College Majors 2026** dataset — a comprehensive record of U.S. postsecondary programs covering earnings, student debt, employment outcomes, and AI exposure across occupations.

The goal is not just to describe the data, but to extract **actionable insights** relevant to students, policymakers, and anyone thinking about the ROI of higher education in an AI-driven economy.

---

## 🔍 Key Questions Explored

- Which fields of study deliver the highest earnings 4 years post-graduation — and which carry the most financial risk?
- Does higher AI exposure in linked occupations translate to better graduate earnings?
- How do debt-to-earnings ratios vary across institution types, credential levels, and regions?
- Which programs offer the best financial value relative to their cost?

---

## 📁 Repository Structure

```
college-major-2026/
│
├── data/
│   ├── college_majors_2026.csv          # Raw dataset (source: linked below)
│   └── cleaned_college_majors.csv       # Cleaned & processed output
│
├── notebooks/
│   └── college_majors_analysis.ipynb    # Full analysis notebook (Colab-ready)
│
├── dashboard/
│   └── college_majors_powerbi.pbix      # Interactive Power BI dashboard
│
├── memo/
│   └── insights_memo.md                 # Key findings written as a business memo
│
├── README_EN.md                            # English version (this file)
└── README_VI.md                         # Vietnamese version
```

---

## 🛠️ Tech Stack & Skills Demonstrated

| Area | Tools / Methods |
|---|---|
| Data cleaning & wrangling | Python, pandas — handling 228K rows, quoted fields, missing values, type coercion |
| Exploratory Data Analysis | seaborn, matplotlib — distributions, correlation, outlier detection |
| Statistical analysis | Pearson correlation, cohort filtering, percentile benchmarking |
| Business insight | Debt-to-earnings framing, AI exposure segmentation, regional comparison |
| Data visualization | Power BI — interactive dashboard with slicers by field, state, credential type |

---

## 💡 Selected Findings

> Full write-up available in [`memo/insights_memo.md`](./memo/insights_memo.md)

- **Engineering and Computer Science** programs consistently outperform national median earnings — but the gap narrows significantly when adjusting for student debt levels.
- **AI exposure alone is a weak predictor of earnings** (Pearson r ≈ 0.18–0.25). The field of study and credential level explain far more variance.
- **Private for-profit institutions** show the worst debt-to-earnings ratios on average, despite similar earnings outcomes compared to public schools in the same CIP category.
- Several **short-term certificate programs** in allied health and skilled trades outperform 4-year bachelor's degrees on debt-adjusted return — a counterintuitive result worth attention.

---

## 📊 Dashboard Preview

> *Power BI dashboard — import `college_majors_powerbi.pbix` to explore interactively*

The dashboard includes:
- Earnings distribution by field of study and credential level
- Debt-to-earnings heatmap by institution type × region
- AI exposure vs. earnings scatter with field-of-study filter
- Top / bottom 10 programs by financial ROI

---

## 📂 Dataset

**Source:** [College Majors 2026: Earnings, Debt, Jobs, AI — Kaggle](https://www.kaggle.com/)  
**Size:** ~228,000 rows × 72 columns  
**Coverage:** U.S. postsecondary programs, outcomes measured 1, 4, and 5 years post-enrollment  
**Key fields:** `median_earnings_4yr_usd`, `median_debt_usd`, `debt_to_earnings_4yr`, `ai_software_occupation_share`

---

## 🚀 Run It Yourself

The notebook is designed to run on **Google Colab** with zero setup:

1. Upload `college_majors_2026.csv` to your Colab session
2. Open `notebooks/college_majors_analysis.ipynb`
3. Run all cells — cleaned CSV and charts export automatically

```python
# Or load from Google Drive
from google.colab import drive
drive.mount('/content/drive')
df = pd.read_csv('/content/drive/MyDrive/college_majors_2026.csv', low_memory=False)
```

---

## 👤 About

**6 months in as a Business Analyst** — this project reflects how I approach data work: starting from a real question, not just a dataset.

I'm interested in roles where analysis connects directly to decisions — not just dashboards for dashboards' sake.

📎 [LinkedIn](#) · 📧 [Email](#)
