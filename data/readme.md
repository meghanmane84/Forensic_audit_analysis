# Data Directory

This directory is intended to hold the raw financial transaction data used for the forensic audit analysis.

## 📊 Dataset Information
The project utilizes the **PaySim Synthetic Financial Dataset** from Kaggle.
* **Filename:** `PS_20174392719_1491204439457_log.csv`
* **Source:** [Synthetic Financial Datasets For Fraud Detection (Kaggle)](https://www.kaggle.com/datasets/ealaxi/paysim1)

## 📥 How to Add the Data
Due to GitHub's file size limits, the raw CSV file is not included in this repository. To run the analysis, follow these steps:

1. **Download** the dataset from the Kaggle link provided above.
2. **Place** the CSV file into this `/data` folder.
3. **Verify** the filename matches the path used in the notebook: `data/loan_data.csv` (or update the path in `Forensic_audit.ipynb` to match your local setup).

## 📋 Data Structure Reference
The engine expects the following key columns for forensic analysis:
* `amount`: Transaction value.
* `oldbalanceOrg` / `newbalanceOrig`: Balance flow for the originator.
* `oldbalanceDest` / `newbalanceDest`: Balance flow for the destination.
* `type`: Categorical type of transaction (e.g., TRANSFER, CASH_OUT).
* `step`: Time unit (used to engineer the `hour` feature).

## ⚠️ Important Note
This data is used to engineer **Forensic Velocity** and **Balance Error** metrics. Ensure the CSV is not renamed, as the notebook relies on these specific headers to calculate fund-flow discrepancies.
