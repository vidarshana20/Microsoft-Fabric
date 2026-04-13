# Smart Property Management Platform — Microsoft Fabric

An end-to-end analytics platform built on Microsoft Fabric for a property management use case, covering data engineering, SQL warehousing, Power BI reporting, and ML prediction.

---

## What's Built

### Spark Data Engineering
- Loaded 4 CSV datasets into OneLake Lakehouse
- Cleaned and standardized data using PySpark notebooks
- Saved as Delta tables for downstream consumption

### Data Warehouse (SQL)
Designed a star schema with:
- `DimProperty` — property details across 5 states
- `DimTenant` — tenant lease, income, and credit data
- `FactRentPayments` — 4,272 payment records with status tracking
- `FactMaintenance` — 600 maintenance requests with priority and cost

5 analytical SQL queries:
| Query | Techniques Used |
|---|---|
| Late Payment Rate by Property | CTE + DENSE_RANK |
| Monthly Revenue Trend | Window function + Running Total |
| Tenant Risk Segmentation | Multi-CTE + CASE classification |
| Maintenance Performance | DENSE_RANK by resolution speed |
| Portfolio Scorecard | 3-CTE + A/B/C/D grading |

### Power BI Dashboard
- Connected via Direct Lake to Fabric Warehouse
- 5 DAX measures (Total Revenue, Late Payment Rate, Avg Satisfaction, etc.)
- 4 visuals: revenue trend, payment status donut, maintenance by priority, high-risk property table

### Machine Learning (Fabric Data Science)
- **Model:** Random Forest Classifier (PySpark MLlib)
- **Target:** Predict late/failed rent payments
- **Features:** credit score, annual income, monthly rent, lease term
- **Results:** AUC 0.8527 · Accuracy 85.2% · F1 0.7990
- **Tracked with:** MLflow experiment logging
- **Key finding:** Identified and corrected data leakage in v1 (AUC 1.0 → removed `days_late` feature) → v2 is the production-ready model

---

## Dataset

| File | Rows | Description |
|---|---|---|
| properties.csv | 100 | Properties across MI, OH, IN, IL, WI |
| tenants.csv | 400 | Lease, income, credit score data |
| rent_payments.csv | 4,272 | 24 months, On Time / Late / Failed |
| maintenance_requests.csv | 600 | Priority, cost, resolution time |

---

## Tech Stack

| Layer | Tools |
|---|---|
| Data Engineering | PySpark, Delta Lake, OneLake |
| Data Warehouse | Fabric Warehouse, T-SQL |
| BI & Reporting | Power BI, DAX, Direct Lake |
| Machine Learning | PySpark MLlib, MLflow |
| Platform | Microsoft Fabric |

---

## How to Run

1. Download the 4 CSV files from the `/data` folder
2. Upload them into a Fabric Lakehouse under `Files/`
3. Run `01_Data_Cleaning.ipynb` to clean and save Delta tables
4. Open the Warehouse and run the SQL scripts in `/sql/`
5. Connect Power BI to the Warehouse via Direct Lake
6. Run `02_ML_LatePayment.ipynb` to train and log the ML model

---

## Future Improvements

- Add Data Factory pipeline for automated ingestion
- Build real-time event stream with KQL and Even
