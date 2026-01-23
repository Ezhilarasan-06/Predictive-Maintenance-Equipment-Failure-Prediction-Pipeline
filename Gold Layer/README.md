## 🥇 Gold Layer – Business & ML Consumption Layer

### 🎯 Purpose
The Gold layer represents the **final, business-consumable output** of the Predictive Maintenance pipeline.

It converts raw ML predictions into **actionable insights** that help manufacturing teams:
- Identify high-risk equipment
- Prioritize maintenance actions
- Reduce unplanned downtime
- Optimize operational cost

This layer is designed for **decision-making, dashboards, and reporting**.

---

### 🔄 Input Sources
- **Silver Feature Table:** `silver_engine_features`
- **ML Predictions Table:** `ml_engine_predictions`
- **Failure Probability Output:** Derived from Spark ML probability vectors

---

### 🧠 Business Logic Applied

The Gold layer applies domain-driven logic on top of ML outputs:

#### 🔢 Failure Probability Extraction
- Extracts failure probability from Spark ML `probability` vector
- Represents likelihood of engine failure in upcoming cycles

#### 🚦 Risk Classification
Engines are categorized based on failure probability:

| Risk Level | Condition |
|----------|-----------|
| LOW | Failure Probability < 0.30 |
| MEDIUM | 0.30 ≤ Probability < 0.70 |
| HIGH | Probability ≥ 0.70 |

> ⚠ Thresholds are configurable based on business tolerance

---

### 🏗️ Gold Tables Created

#### 1️⃣ Equipment Risk Score Table
**Table Name:** `gold_equipment_risk_scores`

| Column | Description |
|------|------------|
| engine_id | Unique engine identifier |
| cycle | Engine operating cycle |
| failure_probability | Predicted probability of failure |
| risk_level | LOW / MEDIUM / HIGH |
| prediction | ML model output (0 / 1) |

---

#### 2️⃣ Fleet Risk Summary Table
**Table Name:** `gold_fleet_risk_summary`

Aggregated view for dashboards:

| Metric | Description |
|------|------------|
| total_engines | Total engines monitored |
| high_risk_engines | Engines requiring urgent attention |
| medium_risk_engines | Engines to be monitored |
| low_risk_engines | Healthy engines |
| snapshot_date | Reporting date |

---

### 📊 Dashboard Consumption

The Gold layer directly powers **Databricks SQL dashboards**:

#### 📈 Dashboard 1 – Fleet Health Overview
- Total engines by risk level
- Failure risk distribution
- Maintenance prioritization view

#### 📉 Dashboard 2 – Engine Risk Trend
- Failure probability vs cycle
- Individual engine degradation trends

#### 🚨 Dashboard 3 – High-Risk Alert View
- List of engines in HIGH risk
- Sorted by failure probability
- Used by maintenance planners

---

### 🛡️ Data Quality & Validation (Gold)

| Check | Description |
|----|------------|
| Probability Range | Values must be between 0 and 1 |
| Risk Mapping | Probability aligns with risk thresholds |
| Record Completeness | No missing engine_id or cycle |
| Snapshot Integrity | Latest cycle used per engine |

All validation failures are logged for audit purposes.

---

### ✅ Output Consumers
- Maintenance Operations Teams
- Reliability Engineers
- Business Dashboards
- Executive Reporting

---

### 🏁 Final Outcome
The Gold layer transforms **machine learning outputs into business intelligence**, enabling proactive maintenance decisions and measurable cost savings.

This completes the **end-to-end Predictive Maintenance Pipeline**.
