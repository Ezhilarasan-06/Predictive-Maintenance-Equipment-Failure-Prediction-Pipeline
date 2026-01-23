## 🥉 Bronze Layer – Raw Data Ingestion

### 🎯 Purpose
The Bronze layer represents the **single source of truth** for the entire pipeline.  
Its role is to ingest raw sensor data **exactly as received**, without any transformation or business logic applied.

This ensures:
- Data traceability
- Auditability
- Reprocessing capability in case of downstream changes

---

### 📥 Data Ingestion

**Source**
- NASA Turbofan Engine Degradation Dataset (CMAPSS)

**Input Format**
- Text files containing:
  - Engine ID
  - Cycle number
  - Operational settings
  - Multiple sensor readings

**Ingestion Approach**
- Data is loaded using Apache Spark
- Schema is explicitly defined to avoid inference issues
- Data is stored in **Delta format** for reliability and ACID compliance

---

### 🧱 Storage Design

- **Format:** Delta Lake
- **Layer:** Bronze
- **Partitioning:** Optional (engine_id)
- **Naming Convention:** `bronze_engine_sensor_data`

> 📌 The Bronze layer preserves **raw granularity** and historical accuracy.

---

### 🛡️ Data Quality Checks (Bronze)

Basic validation rules are applied to ensure ingestion correctness:

| Check Type | Rule |
|----------|------|
| Null Check | `engine_id` and `cycle` must not be null |
| Range Check | Sensor values must fall within expected physical ranges |
| Duplicate Check | No duplicate `(engine_id, cycle)` records |
| Record Count | Source vs ingested count reconciliation |

---> Any failed checks are logged but **do not modify the raw data**.

---

### 📊 Audit & Control Logging

For each ingestion run:
- Record counts are captured
- Validation status is recorded
- Ingestion timestamp is stored

This allows:
- Easy debugging
- Historical run tracking
- End-to-end pipeline observability

---

### 🔑 Key Design Principles

- **No transformations**
- **No aggregations**
- **No business logic**
- **Raw data fidelity preserved**

> *“If the Bronze layer is wrong, everything else is wrong.”*

---

### ✅ Output

- A clean, reliable Delta table containing raw sensor data
- Ready for downstream processing in the Silver layer

---

