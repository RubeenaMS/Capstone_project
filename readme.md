# Strategic Customer Retention Analytics

An end-to-end data science pipeline designed to diagnose, mathematically verify, and predict customer churn. This project moves beyond baseline descriptive metrics to isolate the root operational catalysts behind portfolio attrition, establishing a proactive framework to safeguard recurring revenue.

---

## 📈 Executive Summary & Business Impact

Initial analysis of the 500-customer profile matrix identified a **10.60% macroscopic churn rate** (53 total account dropouts). While a 10.60% churn rate may initially seem manageable, an account deep-dive reveals that churn is disproportionately concentrated within premium-tier subscribers. 

This localized dropout results in an immediate leak of **$6,878.00 in Monthly Recurring Revenue (MRR)**, exposing the organization to an annualized capital leakage of **$82,536.00**. This project provides a data-backed blueprint to systematically plug this revenue drain.

---

## 🛠️ Project Architecture & Pipeline

The repository is structured into an end-to-end data pipeline divided into three primary functional layers:

1. **Data Engineering Layer (`data_cleaning.py`)**
   * Standardizes column arrays by stripping accidental text-trailing white spaces.
   * Normalizes structural categorical parameters (`Contract`, `PaymentMethod`, `PaperlessBilling`) to guarantee consistent grouping analysis.
   * Employs row-wise verification to eliminate exact-match duplicates and safeguard downstream statistical variance.
   * Outputs a clean baseline array to `data/cleaned_data.csv`.

2. **Exploratory Diagnostics Layer (`eda_visuals.py`)**
   * Generates continuous distribution plots identifying a highly critical **"onboarding risk cliff"** during the initial six months of subscription activation.
   * Evaluates feature interdependencies via a Pearson correlation matrix and tracks Customer Lifetime Value (LTV) horizons across continuous timelines.
   * Constructs stacked frequency histograms demonstrating intense volume swelling at premium fee thresholds ($120+), flagging widespread "price fatigue."

3. **Statistical Suite & Predictive Engine (`predictive_modeling.py`)**
   * Runs an unequal variance Welch's t-test to mathematically validate pricing disparities.
   * Configures a multivariate maximum likelihood estimation (MLE) Logistic Regression model to concurrently weigh continuous hazards and isolate structural protective shields.

---

## 🔬 Core Insights & Statistical Proofs

* **The Pricing Fatigue Proof:** Retained subscribers face an average monthly fee of **$111.72**, whereas churned subscribers average **$129.77**. Because the unequal variance Welch's t-test yields high significance ($p \le 0.05$), we officially **reject the Null Hypothesis ($H_0$)**. The $18.05 cost premium is mathematically proven to be a direct driver of attrition rather than random variation.
* **The Structural Shielding Effect:** Multivariate logistic regression models confirm that while high monthly pricing operates as a continuous risk multiplier, long-term tenure builds inherent loyalty equity. Crucially, fixed long-term agreements (1-Year and 2-Year contract plans) act as the organization's strongest statistical barriers against cancellation events.

---

## 🎯 Strategic Recommendations

1. **Onboarding Safekeeping:** Realign customer success parameters from reactive ticketing to automated lifecycle alerts. Trigger proactive customer health reviews at months 2 and 5 to guide volatile accounts safely past the initial 6-month risk cliff.
2. **Contractual Migration Campaigns:** Deploy a value-exchange marketing push offering a 10% monthly fee discount to Month-to-month subscribers who commit to a stable 1-Year term. Regression weights prove that locking in a fixed agreement drops a customer's risk profile by over 80%, far outweighing the localized margin discount.

---

## 🚀 Getting Started & Installation

### Prerequisites
Ensure you have Python installed on your local machine (recommended version 3.9+). 

### Project Directory Structure

.
├── data/
│   ├── raw_data.csv             # Source unmerged input data files
│   └── cleaned_data.csv         # Processed output array used for modeling
├── notebooks/
│   ├── 1_data_cleaning.ipynb    # Data ingestion, cleaning, and formatting script
│   ├── 2_eda.ipynb              # Exploratory visual and core distribution plots
│   └── 3_analysis.ipynb         # Hypothesis verification and logistic regression tests
├── reports/
│   ├── executive_summary.pdf    # 1-page high-level executive brief
│   └── technical_report.pdf     # Full-length technical methodology documentation
└── presentations/
    └── business_presentation.pptx # Final executive stakeholder slide deck

    ---

### Installation
1. Clone this repository to your local system.
2. Navigate to the root directory and install the exact, locked dependency versions via `pip`:
```bash
   pip install -r requirements.txt

   