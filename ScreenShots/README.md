# 📸 Pipeline Execution Screenshots

This section captures **visual proof of execution** for each stage of the Predictive Maintenance pipeline built using **Databricks + Spark ML + Delta Lake**.

The screenshots demonstrate **data ingestion, transformation, modeling, and prediction outputs**.

---

## 🥉 Bronze Layer – Raw Data Ingestion

### Purpose
The Bronze layer ingests **raw NASA CMAPSS sensor data** into Delta tables without any transformation.

### What the Screenshot Shows
- Successful file ingestion into Databricks
- Raw schema with:
  - `engine_id`
  - `cycle`
  - operational settings
  - sensor columns
- Data stored in **Delta format**

### Screenshot Includes
- Spark DataFrame preview
- Record count validation
- Bronze Delta table creation

📷 *Screenshot: Bronze data ingestion output*

---

## 🥈 Silver Layer – Feature Engineering

### Purpose
The Silver layer cleans and enriches raw data to make it **ML-ready**.

### What the Screenshot Shows
- Feature engineering logic execution
- Derived columns:
  - Remaining Useful Life (RUL)
  - rolling averages
  - normalized sensor values
- Cleaned & structured dataset

### Screenshot Includes
- Transformed DataFrame preview
- Feature columns added
- Silver Delta table write confirmation

📷 *Screenshot: Silver feature engineering output*

---

## 🥇 Gold Layer – Business Aggregations

### Purpose
The Gold layer represents **business-consumable data** for dashboards and monitoring.

### What the Screenshot Shows
- Engine-level aggregation
- Risk classification:
  - LOW
  - MEDIUM
  - HIGH
- Failure probability outputs

### Screenshot Includes
- Engine risk score table
- Aggregated failure metrics
- Gold Delta table creation

📷 *Screenshot: Gold risk score table*

---

## 🤖 ML Layer – Model Training & Prediction

### Purpose
The ML layer trains a **failure prediction model** and generates predictions for unseen engine data.

### What the Screenshot Shows
- Model training execution (Spark ML)
- Prediction output with:
  - `prediction`
  - `probability`
  - `failure_probability`
- Class distribution of predictions

### Screenshot Includes
- Model pipeline stages
- Prediction count summary
- Sample inference results

📷 *Screenshot: ML prediction output*


