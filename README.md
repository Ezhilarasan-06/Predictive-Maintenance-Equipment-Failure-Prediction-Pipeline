# 🚀 Predictive Maintenance – Equipment Failure Prediction Pipeline

> **“Machines don’t fail suddenly — they whisper before they scream.”**  
This project listens to those whispers.

---

## 🧠 Why This Project Exists

In manufacturing, **unexpected machine failure = lost money, lost time, lost trust**.

This project builds a **data-driven early warning system** that predicts **when a machine is approaching failure**, using real-world sensor data and scalable big-data architecture.

Instead of reacting *after* breakdowns, businesses can now:
- 🔧 Schedule maintenance proactively  
- ⏱️ Reduce unplanned downtime  
- 💰 Save operational costs  

---

## 🏭 Business Problem

Manufacturing companies operate hundreds of machines generating massive sensor data.  
The challenge is **turning raw signals into actionable failure predictions**.

This solution answers one critical question:

> **“Is this machine safe… or is it approaching failure?”**

---

## 📊 Data Source

- **Dataset:** NASA Turbofan Engine Degradation Dataset (CMAPSS)
- **Type:** Multivariate time-series sensor data
- **Domain:** Manufacturing / Aerospace
- **Reality Factor:** Industry-grade dataset widely used for predictive maintenance research.

---

## 🏗️ End-to-End Architecture

This project follows a **production-grade data engineering + ML architecture**, inspired by real Databricks implementations.

### High-Level Flow
```

Raw Sensor Data (NASA CMAPSS)
↓
Bronze Layer – Raw Ingestion
↓
Silver Layer – Feature Engineering
↓
Failure Label Generation (RUL-based)
↓
ML Training (Spark ML)
↓
Batch Inference
↓
Risk Scoring & Dashboards

```
📌 **Design Principle:**  
Each layer has a **single responsibility**, making the pipeline scalable, debuggable, and production-ready.

---

## 🧱 Pipeline Breakdown

### 🥉 Bronze Layer – Raw Truth
- Ingest raw sensor data
- Preserve original structure
- Perform basic data quality checks

> *No transformations. No assumptions. Just clean ingestion.*

---

### 🥈 Silver Layer – Feature Engineering
- Rolling statistics (mean)
- Sensor deltas (change over time)
- Feature normalization

> *This layer converts raw noise into meaningful signals.*

---

### 🏷️ Failure Label Generation
- Remaining Useful Life (RUL) calculated per engine
- Binary failure label generated using threshold logic:
  - `0 → Safe`
  - `1 → Approaching Failure`

> *This step teaches the model what “failure looks like”.*

---

### 🤖 ML Training Pipeline (Spark ML)
- Feature vector assembly
- Binary classification model training
- Model evaluation and validation

> *The model learns degradation patterns, not just raw values.*

---

### 🔮 Batch Inference
- Predict failure probability for each engine cycle
- Classify equipment risk: <br>
  🟢 LOW <br>
  🟡 MEDIUM <br>
  🔴 HIGH <br>

---

### 🏆 Gold Layer – Business-Ready Outputs
- Equipment risk score table
- Prediction summary tables
- Dashboard-ready datasets

> *This is what decision-makers actually see.*

---

## 📈 Dashboards

### 📊 Dashboard 1: Fleet-Level Equipment Health Monitoring
**Audience:** Operations & Management  
- Overall fleet health
- Risk distribution across machines

---

### 📉 Dashboard 2: Model Monitoring & Insights
**Audience:** Reliability Engineers  
- Failure probability vs cycle
- Early degradation detection

---

### 🚨 Dashboard 3: Predictive Maintenance – Engine Health Details
**Audience:** Maintenance Team  
- Engines requiring immediate attention
- Prioritized by risk score

---

## 🛡️ Data Quality & Validation Framework

This project doesn’t just predict — **it validates**.

### Data Quality Strategy
- Validation at every layer
- Prevents garbage-in → garbage-out
- Ensures ML reliability

### Validation Coverage
- Raw ingestion accuracy (Bronze)
- Feature correctness (Silver)
- Label integrity (RUL logic)
- Prediction sanity checks (0 ≤ probability ≤ 1)

---

## 🧾 Audit & Control Tables

Every pipeline run is tracked:
- Record counts
- Validation status
- Execution timestamps

> *This makes the system explainable, auditable, and production-ready.*

---

## 🧪 Technologies Used

| Category | Technology |
|--------|------------|
| Processing | Apache Spark (PySpark) |
| Storage | Parquet / Delta Lake 
| ML Pipeline | Logistic Regression |
| Analytics | Databricks SQL |
| Visualization | Databricks Dashboards |
| Version Control | Git & GitHub |

---

## 🎯 Final Outcome

- ✅ Predict machine failure **before breakdown**
- ✅ Convert sensor data into **actionable insights**
- ✅ Enable **data-driven maintenance decisions**

---

## 🔚 Final Thought

This is **not just a project**.  
This is a **mini version of what real manufacturing analytics teams build**.

