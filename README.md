# Microsoft-Fabric
# 🏢 Real-Time Property Operations Analytics Platform (Microsoft Fabric)

## 📌 Overview

This project demonstrates an **end-to-end data platform built using Microsoft Fabric**, integrating batch processing, real-time analytics, machine learning, and business intelligence for a property management use case.

The system analyzes property operations including **rent payments, tenant activity, maintenance requests, and real-time building events**, enabling data-driven decision-making and automated alerts.

---

## 🚀 Key Features

* 🔄 Data ingestion using **Data Factory**
* ⚡ Data transformation using **Spark (Data Engineering)**
* 🏢 Data modeling using **Data Warehouse (SQL)**
* 🤖 Predictive analytics using **Data Science (MLflow)**
* 📡 Real-time event processing using **KQL/Eventstreams**
* 📊 Interactive dashboards using **Power BI**
* 🚨 Automated alerts using **Data Activator**

---

## 🏗️ Architecture

### Batch Pipeline

```
CSV Files → Data Factory → Lakehouse (OneLake)
          → Data Engineering (Spark)
          → Data Warehouse (SQL Tables)
          → Power BI Dashboard
```

### Real-Time Pipeline

```
Event Stream → Eventstream → KQL Database
             → Real-Time Dashboard → Data Activator Alerts
```

---

## 📂 Dataset

The project uses simulated property management data:

* **Properties** – Property details (location, type, units)
* **Tenants** – Tenant information and lease data
* **Rent Payments** – Payment status and trends
* **Maintenance Requests** – Issue tracking and resolution

---

## ⚙️ Tech Stack

**Languages & Tools**

* Python (PySpark, Pandas)
* SQL

**Microsoft Fabric Components**

* Data Factory
* Synapse Data Engineering (Spark)
* Synapse Data Warehousing
* Synapse Data Science (MLflow)
* Real-Time Analytics (KQL)
* Power BI
* Data Activator
* OneLake

---

## 🔄 Data Pipeline

### 1. Data Ingestion

* Loaded CSV datasets using Data Factory pipelines
* Scheduled batch ingestion

### 2. Data Transformation

* Cleaned and transformed data using Spark notebooks
* Created curated datasets (clean schema, standardized formats)

### 3. Data Warehousing

* Designed star schema:

  * `DimProperty`
  * `DimTenant`
  * `FactRentPayments`
  * `FactMaintenance`

### 4. Data Analysis

* SQL queries to analyze:

  * Rent collection trends
  * Late payments
  * Maintenance workload

---

## 🤖 Machine Learning (Data Science)

Built a predictive model to:

* Identify **tenants likely to make late payments**

Features used:

* Payment history
* Tenant demographics
* Lease duration

Tracked experiments using **MLflow**

---

## 📡 Real-Time Analytics

Simulated streaming data such as:

* Maintenance alerts (leaks, faults)
* Payment failures
* Occupancy spikes

Processed using:

* Eventstreams
* KQL Database

---

## 📊 Dashboard (Power BI)

Developed dashboards to visualize:

* Rent collection performance
* Late payment percentage
* Maintenance trends
* Property occupancy

---

## 🚨 Data Activator

Configured automated rules:

* Alert when **multiple maintenance issues occur**
* Notify when **rent payment fails**
* Trigger alerts for **high occupancy conditions**

---

## 📈 Business Impact

* Improved visibility into property operations
* Enabled proactive maintenance handling
* Reduced manual monitoring through automation
* Supported data-driven decision-making

---

## 🧠 Key Learnings

* Built an **end-to-end modern data platform**
* Integrated batch and real-time analytics
* Applied machine learning in operational workflows
* Designed scalable data architecture using Fabric

---

## ▶️ How to Run

1. Upload CSV files into Fabric Lakehouse
2. Create Data Factory pipeline for ingestion
3. Run Spark notebooks for transformation
4. Load curated data into Warehouse tables
5. Connect Power BI to visualize data
6. Simulate real-time events using Eventstreams
7. Configure Data Activator rules

---

## 📌 Future Improvements

* Integrate real IoT sensor data
* Deploy ML model as a real-time service
* Add anomaly detection for maintenance
* Implement role-based dashboards

---

## 👤 Author

**Aswin Gunasekaran**
M.S. Data Science – University of Michigan Dearborn
