## 🤖 Machine Learning Layer – Failure Prediction

### 🎯 Objective
The Machine Learning layer predicts **imminent equipment failure** using historical sensor data from aircraft engines.

Instead of predicting exact failure time, the model classifies whether an engine is:
- **Operating normally**
- **Close to failure** (within a defined Remaining Useful Life threshold)

This enables **early maintenance intervention**.

---

### 📊 Problem Formulation
- **Type:** Supervised Binary Classification
- **Target Variable:** `failure_label`
  - `0` → Safe operation
  - `1` → Near failure (RUL ≤ threshold)

---

### 📁 Datasets Used

| Dataset | Purpose |
|------|-------|
| `train_FD001` | Model training |
| `test_FD001` | Inference / prediction |
| `RUL_FD001.txt` | True Remaining Useful Life for test engines |

---

### 🏷️ Label Generation Logic

Failure labels are derived using **Remaining Useful Life (RUL)**:<br>
RUL = max_cycle_per_engine − current_cycle


#### Failure Threshold Logic:
- `failure_label = 1` → RUL ≤ 30 cycles  
- `failure_label = 0` → RUL > 30 cycles  

This approach simulates **real-world predictive maintenance**, where failures are anticipated before breakdown.

---

### 🧠 Feature Set
Features are sourced from the **Silver layer** and include:
- Selected sensor readings
- Operational settings
- Engine cycle count
- Aggregated rolling statistics (if applicable)

All features are assembled using Spark ML pipelines.

---

### 🏗️ ML Pipeline (Spark ML)

The ML pipeline consists of:

1. **VectorAssembler**
   - Combines selected features into a single feature vector

2. **Feature Scaling**
   - Normalizes sensor values to improve model stability

3. **Classifier**
   - Logistic Regression (binary classification)

4. **Pipeline API**
   - Ensures reproducibility and clean workflow

---

### 🧪 Model Training

- **Framework:** Apache Spark MLlib
- **Algorithm:** Logistic Regression
- **Training Data:** `train_FD001`
- **Target Column:** `failure_label`

The model learns degradation patterns that indicate **approaching failure**.

---

### 📈 Prediction Output

The trained model generates:
- `prediction` → 0 or 1
- `probability` → likelihood of failure

Example:<br>
prediction = 1<br>
failure_probability = 0.82


This probability is later used for **risk scoring**.

---

### 📊 Model Output Summary

| Prediction | Meaning |
|---------|--------|
| 0 | Engine operating safely |
| 1 | Engine close to failure |

Sample distribution:<br>
prediction = 0 → majority (healthy engines)<br>
prediction = 1 → minority (at-risk engines)


This imbalance reflects real-world scenarios.

---

### 🔍 Validation Checks (ML)

- Feature completeness check
- No null values in ML inputs
- Probability values within [0,1]
- Prediction consistency across cycles

All validations are logged for auditability.

---

### 🔄 Batch Inference

- Applied on `test_FD001`
- Generates cycle-wise predictions per engine
- Results stored for Gold layer consumption

---

### 🚀 Business Impact

The ML layer enables:
- Early failure detection
- Reduced unplanned downtime
- Data-driven maintenance scheduling
- Scalable deployment using Spark

---

### 🏁 Output Consumers
- Gold Risk Scoring Layer
- Databricks Dashboards
- Maintenance Planning Teams
