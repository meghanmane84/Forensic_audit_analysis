# Forensic Financial Audit & Anomaly Detection
### Automated Fraud Detection & Ledger Integrity using Unsupervised Machine Learning

## 🎯 Project Overview
In large-scale financial environments, manual auditing is insufficient for detecting sophisticated fraud. This project implements a **Consulting-Grade Forensic Engine** designed to identify "red flag" transactions within a dataset of over 6 million records. By combining 200-year-old accounting principles with modern unsupervised machine learning, the engine provides a multi-layered defense against financial manipulation.

## 📊 Dataset & Flow of Funds
The analysis utilizes the **PaySim Synthetic Financial Dataset**, which simulates mobile money transactions (TRANSFER, CASH_OUT, etc.) based on real-world banking logs.

* **Forensic Feature Engineering:** I engineered "Balance Error" features (`errorBalanceOrg`, `errorBalanceDest`) to quantify the discrepancy between expected and actual account balances—a primary indicator of fund diversion.
* **Temporal Context:** Integrated an `hour` feature to analyze time-based spending patterns and identify high-risk nocturnal transactions.

## 🕵️ Advanced Forensic Methodology

### 1. Statistical Screening: Benford’s Law
The engine conducts a **Ledger Integrity Check** using Benford's Law to evaluate if leading digits follow a natural logarithmic distribution. Significant deviations serve as a "macro" red flag for systemic data manipulation or threshold-testing.



### 2. Behavioral Forensic: Last-Digit Preference
To detect "Psychological Rounding," I implemented a **Digit-Preference Analysis** on trailing digits. In a natural ledger, trailing digits should follow a uniform distribution; spikes in specific digits (like '0' or '9') indicate intentional human intervention.



### 3. Temporal Dynamics: Transaction Velocity (Layering Detection)
Fraud often involves "Layering"—moving money rapidly through accounts to distance it from the source.
* **tx_velocity:** Tracks the frequency of transactions per account within a rolling temporal window.
* **amount_velocity:** Monitors the cumulative volume of funds moved by an account in a short period.
* **Impact:** This identifies "burst" patterns where an account moves 10x its historical daily average in a few hours, a key indicator of money laundering.



### 4. Unsupervised Anomaly Detection: Isolation Forest
Using the **Isolation Forest** algorithm, the engine isolates "different and few" observations. Unlike supervised models, this requires no labels, making it ideal for detecting "Zero-Day" fraud patterns.



### 5. Explainable AI (XAI): SHAP Integration
To move beyond "Black Box" results, I integrated **SHAP (SHapley Additive exPlanations)**.
* **Global Drivers:** Identifies which features (e.g., Balance Error vs. Velocity) are the biggest fraud indicators.
* **Local Reason Codes:** Generates **Waterfall Plots** for flagged transactions to provide human auditors with clear mathematical justification for every anomaly.



## 📈 Industrial Impact & Serious Analysis
* **AML Compliance:** This methodology aligns with **Anti-Money Laundering (AML)** standards by flagging "Structuring" behavior (multiple transactions just below reporting thresholds).
* **Operational Efficiency:** The system narrowed 6 million entries to the top **1% most suspicious transactions** (4,590 flags), reducing manual audit workload by over 99%.
* **Forensic Validation:** SHAP analysis confirmed that `errorBalanceOrg` was the most critical signal, validating the "Balance Discrepancy" hypothesis.

## 🛠 Tech Stack
* **Language:** Python
* **Machine Learning:** Scikit-Learn (Isolation Forest)
* **Explainability:** SHAP
* **Analysis:** Pandas, NumPy, Scipy
* **Visualization:** Matplotlib, Seaborn

---
**Author:** Meghan Vinayak Mane  
**Background:** MSc Data Science and Analytics (First Class Honours), University College Cork
