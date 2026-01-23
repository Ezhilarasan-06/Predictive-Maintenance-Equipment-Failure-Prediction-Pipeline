# 📦 Dataset Documentation

## 📌 Dataset Name
**NASA Turbofan Engine Degradation Dataset (CMAPSS)**

---

## 🌍 Data Source
Provided by **NASA Prognostics Center of Excellence**

- Domain: Manufacturing / Aerospace
- Use Case: Predictive Maintenance
- Data Type: Multivariate Time-Series Sensor Data

---

## 🎯 Dataset Purpose
The dataset simulates degradation behavior of turbofan engines under different operating conditions.  
It is widely used for:
- Remaining Useful Life (RUL) prediction
- Failure classification
- Predictive maintenance research

---

## 📁 Dataset Files Used

| File Name | Description |
|---------|-------------|
| `train_FD001.txt` | Full run-to-failure data for training |
| `test_FD001.txt` | Partial engine run data for prediction |
| `RUL_FD001.txt` | True RUL values for test engines |

---

## 🏗️ Dataset Structure

Each row represents **one engine cycle**.

### Columns Overview

| Column Type | Description |
|-----------|-------------|
| `engine_id` | Unique engine identifier |
| `cycle` | Time cycle count |
| `op_setting_1..3` | Operational settings |
| `sensor_1..21` | Sensor measurements |

---

## 🏁 Summary

The CMAPSS FD001 dataset provides a **realistic, production-like foundation** for building and demonstrating a complete predictive maintenance pipeline using:
- Delta Lake
- Spark ML
- Databricks Dashboards