# 📊 Dashboards & 📘 Documentation



### 🎯 Dashboard Objective
The dashboards provide **actionable insights** into machine health and failure risks by visualizing ML predictions and engineered features.

They help:
- Reduce unplanned downtime
- Enable proactive maintenance
- Improve operational decision-making

---

## 🧭 Dashboard Overview (Total: 3 Dashboards)

---

### 📊 Dashboard 1: Fleet Health Overview

**Purpose:**  
Provide a high-level snapshot of the overall health of the engine fleet.

**Key Metrics:**
- Total number of engines
- Total prediction records
- Count of engines at risk
- Healthy vs At-Risk engines

**Visuals Used:**
- KPI cards
- Bar chart (prediction distribution)
- Pie chart (risk distribution)

**Business Value:**  
Allows stakeholders to quickly assess **fleet-wide failure risk**.

---

### 📈 Dashboard 2: Engine Degradation Trend

**Purpose:**  
Analyze how failure probability evolves across engine cycles.

**Visual Type:**
- Line chart

**Axes:**
- **X-axis:** Engine Cycle
- **Y-axis:** Failure Probability

**Filters:**
- Engine ID

**Business Value:**  
Enables early detection of degradation trends and failure proximity.

---

### 🚨 Dashboard 3: Failure Risk Monitoring

**Purpose:**  
Track engines nearing failure and prioritize maintenance actions.

**Visuals Used:**
- Risk table with conditional formatting
- Bar chart (risk level count)

**Key Fields:**
- Engine ID
- Cycle
- Failure Probability
- Risk Level (LOW / MEDIUM / HIGH)

**Business Value:**  
Supports data-driven maintenance scheduling.

---

## 🛠️ Dashboard Implementation

- Built using **Databricks SQL Dashboards**
- Data sourced from **Gold Layer Delta tables**
- Interactive filters for real-time analysis

**Primary Table:**
- `gold_equipment_risk_score`

