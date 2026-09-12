# FMCG Sales Analytics — Databricks

> An end-to-end FMCG data engineering and analytics project built on **Databricks**, transforming raw sales data into curated analytical datasets and business insights.

## 📌 Project Overview

This project demonstrates a complete data pipeline for **Parent Company and Child Company** sales data.

The solution follows a **Bronze → Silver → Gold** architecture and supports both **full-load and incremental-load** processing. The curated data is then used for business analytics through a Databricks dashboard and Genie.

### Key highlights

- Layered Bronze, Silver and Gold architecture
- Parent & Child Company data integration
- Dimension and fact data processing
- Full-load and incremental-load pipelines
- Databricks / Unity Catalog setup
- Lakeflow Jobs orchestration
- Business-focused analytics dashboard
- Genie-ready analytical data

---

## 🏗️ Architecture

<p align="center">
  <img src="Dashboard/Screenshot 2026-09-12 122548.png" alt="FMCG Sales Analytics Architecture" width="95%">
</p>

### 🔄 Data Flow

```text
Raw Data
   │
   ▼
Lakeflow Jobs
   │
   ▼
Bronze Layer
   │
   ▼
Silver Layer
   │
   ▼
Gold Layer
   │
   ▼
Parent + Child Company Integration
   │
   ▼
Analytics
   ├── Databricks Dashboard
   └── Genie
```

The architecture separates ingestion, transformation and analytics into clear layers, making the workflow easier to maintain and extend.

---

## ⚙️ Data Engineering

### Dimension Processing

The project processes the following dimensions:

- Customers
- Products
- Pricing

### Fact Processing

Order/fact data is processed using two workflows:

**Full Load**
- Used for initial/historical data processing.

**Incremental Load**
- Used to process newly arriving data without reprocessing the complete historical dataset.

This provides a practical pattern for moving from initial data loading to ongoing pipeline updates.

---

## 🏢 Parent & Child Company Integration

The project handles data from two company sources.

```text
Parent Company
      │
      ▼
Parent Gold Analytics
      │
      ├──────────────┐
                     │
Child Company       │
      │              │
      ▼              │
Bronze → Silver → Gold
      │              │
      └────── Merge ─┘
             │
             ▼
      Consolidated Analytics
```

This demonstrates how Child Company data can be processed independently and then integrated with existing Parent Company analytical data.

---

## 📊 Sales Analytics Dashboard

<p align="center">
  <img src="https://github.com/Kaif-077/FMCG__Sales-Analytics-Databricks/blob/main/Resources/project_architecture.png" alt="Sales Analytics Dashboard" width="95%">
</p>

The dashboard provides business-focused views such as:

- Sales trends over time
- Sales by category
- Top products by sales
- Sales by region/market
- Sales by channel
- Customer sales analysis
- Sales performance summary
- Orders by division/status
- Category performance by channel

### Key KPIs

| KPI | Dashboard Value |
|---|---:|
| Total Revenue | 119.93B |
| Total Orders | 101.21K |
| Total Products Sold | 39.05M |
| Average Order Value | 1.18M |
| Total Customers | 53 |
| Average Price | 4,052.46 |

---

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| **Databricks** | Data engineering and analytics |
| **PySpark / SQL** | Data transformation |
| **Unity Catalog** | Data and catalog management |
| **Lakeflow Jobs** | Pipeline orchestration |
| **Amazon S3** | Data storage |
| **Databricks Dashboards** | Business visualization |
| **Genie** | Natural-language analytics |

---

## 📂 Project Structure

```text
fmcg-sales-analytics-databricks/
│
├── data/
│   ├── parent_company/
│   │   ├── full_load/
│   │   └── incremental_load/
│   └── child_company/
│       ├── full_load/
│       └── incremental_load/
│
├── notebooks/
│   ├── setup/
│   ├── dimension_data_processing/
│   └── fact_data_processing/
│
├── dashboard/
│   ├── sales_analytics_dashboard.pdf
│   └── sales_analytics_dashboard.lvdash.json
│
└── resources/
    ├── project_architecture.png
    └── databricks_project.excalidraw
```

### 📓 Main Notebooks

```text
setup/
├── dim_date_table_creation.ipynb
├── setup_catalog.ipynb
└── utilities.ipynb

dimension_data_processing/
├── 1_customers_data_processing.ipynb
├── 2_products_data_processing.ipynb
└── 3_pricing_data_processing.ipynb

fact_data_processing/
├── 1_full_load_fact.ipynb
└── 2_incremental_load_fact.ipynb
```

---

## 🎯 Project Objective

The objective is to build a scalable FMCG analytics workflow that:

1. Ingests and organizes company sales data.
2. Processes data through Bronze, Silver and Gold layers.
3. Supports both full and incremental processing.
4. Integrates Parent and Child Company data.
5. Produces curated analytical data.
6. Delivers business insights through Databricks dashboards and Genie.

---

## 📁 Project Resources

- **Architecture:** `resources/project_architecture.png`
- **Architecture source:** `resources/databricks_project.excalidraw`
- **Dashboard:** `dashboard/sales_analytics_dashboard.pdf`
- **Dashboard definition:** `dashboard/sales_analytics_dashboard.lvdash.json`

---

## 📧 Contact  

- 💼 **LinkedIn**: [www.linkedin.com/in/mohamedkaif07](https://www.linkedin.com/in/mohamedkaif07)
- 📩 **Email**: [mohamedkaif90832@gmail.com](mailto:mohamedkaif90832@gmail.com)
