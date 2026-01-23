## 🥈 Silver Layer – Feature Engineering

### 🎯 Purpose
The Silver layer transforms raw sensor data from the Bronze layer into **clean, structured, and ML-ready features**.

This layer bridges the gap between **raw telemetry** and **predictive intelligence** by:
- Cleaning inconsistencies
- Engineering time-series features
- Preparing reliable inputs for failure prediction models

---

### 🔄 Input Source
- **Bronze Delta Table:** `bronze_engine_sensor_data`
- Contains raw engine sensor readings per cycle

---

### 🧹 Data Cleaning & Standardization

The following preprocessing steps are applied:

- Removal of duplicate `(engine_id, cycle)` records
- Handling missing or invalid sensor values
- Consistent data type enforcement
- Sorting records by engine lifecycle progression

> ✔ Ensures temporal correctness for time-series analysis

---

### 🧠 Feature Engineering Logic

To capture degradation patterns over time, the following features are created:

#### 📈 Rolling Statistics
- Rolling mean for each sensor
- Windowed over previous N cycles
- Helps smooth noise and highlight long-term trends

#### 🔁 Delta Features
- Difference between current and previous cycle values
- Captures sudden changes and early degradation signals

#### ⚙️ Operational Context
- Operational settings are retained to account for usage conditions
- Enables the model to learn environment-aware behavior

---

### 🧱 Output Schema Highlights

| Feature Type | Examples |
|------------|---------|
| Raw Signals | `op1`, `op2`, `op3` |
| Rolling Features | `s1_roll_mean`, `s2_roll_mean`, … |
| Delta Features | `s1_delta`, `s2_delta`, … |
| Identifiers | `engine_id`, `cycle` |

---

### 🛡️ Data Quality Checks (Silver)

Advanced validation rules ensure feature reliability:

| Validation Type | Rule |
|---------------|------|
| Null Check | No nulls in engineered features |
| Window Consistency | Rolling features must respect cycle order |
| Statistical Sanity | No extreme or infinite values |
| Row Count | Silver ≤ Bronze (no artificial inflation) |

Failures are logged for audit, not silently dropped.

---

### 📊 Audit & Reconciliation

- Feature counts reconciled with Bronze records
- Feature statistics compared against raw signals
- Any mismatch is captured in control tables

This ensures **trustworthy downstream ML behavior**.

---

### ✅ Output

- **Silver Delta Table:** `silver_engine_features`
- Fully ML-ready dataset
- Used directly for:
  - Failure label generation
  - Model training
  - Batch inference



