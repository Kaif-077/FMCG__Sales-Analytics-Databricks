# FMCG Sales Analytics --- Databricks

```{=html}
<p align="center">
```
```{=html}
<h1 align="center">
```
FMCG Sales Analytics
```{=html}
</h1>
```
```{=html}
<p align="center">
```
End-to-end data engineering and analytics project built with Databricks
```{=html}
</p>
```
```{=html}
</p>
```

------------------------------------------------------------------------

## 📌 Overview

This project implements an end-to-end FMCG Sales Analytics solution
using **Databricks**.

The platform processes data for a **Parent Company** and a **Child
Company**, moving data through a layered **Bronze → Silver → Gold**
architecture before making curated data available for analytics and
dashboards.

The project demonstrates:

-   Raw data ingestion
-   Full-load and incremental-load processing
-   Dimension and fact data processing
-   Bronze, Silver and Gold data layers
-   Parent/Child company data integration
-   Unity Catalog setup
-   Lakeflow Jobs orchestration
-   Databricks Dashboards
-   Genie-based analytics

------------------------------------------------------------------------

## 🏗️ Data Pipeline & Architecture

The complete project architecture and data flow are shown below.

```{=html}
<p align="center">
```
`<img src="resources/project_architecture.png" alt="FMCG Sales Analytics project architecture" width="100%">`{=html}
```{=html}
</p>
```
### 🔄 High-Level Data Flow

``` text
                         RAW DATA
                            │
                            ▼
                     ┌──────────────┐
                     │ Lakeflow Jobs│
                     └──────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Bronze Layer  │
                    └───────┬───────┘
                            │
                      Transformation
                            │
                            ▼
                    ┌───────────────┐
                    │ Silver Layer  │
                    └───────┬───────┘
                            │
                      Child Gold Layer
                            │
                            ▼
                    ┌───────────────┐
                    │  Gold Layer   │
                    └───────┬───────┘
                            │
                  Merge with Parent Gold
                            │
                            ▼
              ┌──────────────────────────┐
              │ Parent Gold Analytics    │
              │          Table           │
              └────────────┬─────────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Dashboards / Genie│
                 └───────────────────┘
```

------------------------------------------------------------------------

## 🏢 Business Architecture

The solution separates the processing of the **Parent Company** and
**Child Company** while allowing the Child Company's curated Gold data
to be integrated with the Parent Company's existing Gold Analytics data.

### Parent Company

The Parent Company provides the existing Gold Analytics table used as
part of the consolidated analytical solution.

### Child Company

The Child Company follows the complete processing flow:

**Raw Data → Bronze → Silver → Gold → Merge with Parent Gold**

This architecture makes the solution suitable for onboarding additional
company data into a common analytics environment.

------------------------------------------------------------------------

## 📂 Repository Structure

``` text
fmcg-sales-analytics-databricks/
│
├── data/
│   ├── parent_company/
│   │   ├── full_load/
│   │   └── incremental_load/
│   │
│   └── child_company/
│       ├── full_load/
│       └── incremental_load/
│
├── notebooks/
│   ├── setup/
│   │   ├── dim_date_table_creation.ipynb
│   │   ├── setup_catalog.ipynb
│   │   └── utilities.ipynb
│   │
│   ├── dimension_data_processing/
│   │   ├── 1_customers_data_processing.ipynb
│   │   ├── 2_products_data_processing.ipynb
│   │   └── 3_pricing_data_processing.ipynb
│   │
│   └── fact_data_processing/
│       ├── 1_full_load_fact.ipynb
│       └── 2_incremental_load_fact.ipynb
│
├── dashboard/
│   ├── sales_analytics_dashboard.pdf
│   ├── sales_analytics_dashboard.lvdash.json
│   └── sales_analytics_dashboard_preview.png
│
├── resources/
│   ├── databricks_project.excalidraw
│   └── project_architecture.png
│
└── README.md
```

------------------------------------------------------------------------

## ⚙️ Data Engineering Workflow

### 1. Setup

The setup notebooks establish the project environment and supporting
objects.

-   `setup_catalog.ipynb`
-   `dim_date_table_creation.ipynb`
-   `utilities.ipynb`

### 2. Dimension Processing

The dimension processing layer handles:

-   Customer data
-   Product data
-   Pricing data

Notebooks:

``` text
1_customers_data_processing.ipynb
2_products_data_processing.ipynb
3_pricing_data_processing.ipynb
```

### 3. Fact Processing

The fact-processing layer handles order data through both full and
incremental workflows.

``` text
1_full_load_fact.ipynb
2_incremental_load_fact.ipynb
```

This allows the pipeline to support both initial historical loading and
subsequent incremental data processing.

------------------------------------------------------------------------

## 📊 Dashboard

The project includes a **Sales Analytics Dashboard** for analyzing
business performance.

```{=html}
<p align="center">
```
`<img src="dashboard/sales_analytics_dashboard_preview.png" alt="Sales Analytics Dashboard" width="100%">`{=html}
```{=html}
</p>
```
### Dashboard Analysis

The dashboard provides views including:

-   Sales trend over time
-   Sales by category
-   Sales by region/market
-   Sales by payment/acquisition channel
-   Customer sales analysis
-   Sales performance summary
-   Orders by status/division
-   Category performance by channel
-   Top products by sales

### Key Dashboard KPIs

  KPI                     Value shown in dashboard
  --------------------- --------------------------
  Total Revenue                            119.93B
  Total Orders                             101.21K
  Total Products Sold                       39.05M
  Average Order Value                        1.18M
  Total Customers                               53
  Average Price                           4,052.46

> These values are the metrics displayed in the included dashboard
> snapshot.

The original dashboard export is also available at:

`dashboard/sales_analytics_dashboard.pdf`

------------------------------------------------------------------------

## 🧰 Technology Stack

  Technology                  Usage
  --------------------------- -----------------------------------------
  **Databricks**              Data engineering and analytics platform
  **Unity Catalog**           Catalog and data management
  **Lakeflow Jobs**           Pipeline/job orchestration
  **PySpark / SQL**           Data transformation and processing
  **Amazon S3**               Raw data / object storage
  **Databricks Dashboards**   Business intelligence and visualization
  **Genie**                   Natural-language analytics

------------------------------------------------------------------------

## 🔁 Full Load vs Incremental Load

The project demonstrates two approaches to fact data processing.

### Full Load

Used to process the initial/historical dataset and establish the base
analytical data.

### Incremental Load

Used to process newly arriving data without reprocessing the complete
historical dataset.

This pattern helps demonstrate how an analytics pipeline can move from
an initial historical load to ongoing data ingestion.

------------------------------------------------------------------------

## 🎯 Project Objectives

The main objectives of this project are to demonstrate how to:

1.  Build a structured data engineering pipeline in Databricks.
2.  Organize raw data into company-specific source structures.
3.  Process data through Bronze, Silver and Gold layers.
4.  Separate dimension and fact processing.
5.  Implement both full-load and incremental-load workflows.
6.  Integrate Child Company data with Parent Company Gold analytics.
7.  Build a business-facing analytics dashboard.
8.  Provide a foundation for interactive analytics using Genie.

------------------------------------------------------------------------

## 📁 Data Organization

The repository separates source data by company:

``` text
data/
├── parent_company/
└── child_company/
```

Each company contains dedicated areas for:

``` text
full_load/
incremental_load/
```

This structure keeps source data organized and mirrors the project's
processing strategy.

------------------------------------------------------------------------

## 📈 Analytics Layer

The Gold layer is the primary analytical layer of the architecture.

It provides curated data that can be consumed by:

-   Databricks Dashboards
-   Genie
-   Business analysis
-   Downstream analytical workloads

The architecture therefore separates **data ingestion and
transformation** from **business-facing analytics**.

------------------------------------------------------------------------

## 🚀 Project Highlights

### Data Engineering

-   Layered Bronze/Silver/Gold architecture
-   Dimension and fact processing
-   Full and incremental processing
-   Parent/Child company integration

### Databricks

-   Unity Catalog
-   Lakeflow Jobs
-   Notebook-based development
-   Dashboarding
-   Genie

### Analytics

-   Revenue analysis
-   Order analysis
-   Product performance
-   Customer analysis
-   Category and market analysis
-   Channel analysis
-   Time-based sales trends

------------------------------------------------------------------------

## 🗺️ Project Resources

  ---------------------------------------------------------------------------------------
  Resource                            Location
  ----------------------------------- ---------------------------------------------------
  Architecture diagram                `resources/project_architecture.png`

  Excalidraw architecture             `resources/databricks_project.excalidraw`

  Dashboard export                    `dashboard/sales_analytics_dashboard.pdf`

  Dashboard definition                `dashboard/sales_analytics_dashboard.lvdash.json`

  Dashboard preview                   `dashboard/sales_analytics_dashboard_preview.png`
  ---------------------------------------------------------------------------------------

------------------------------------------------------------------------

## 👨‍💻 Project

**FMCG Sales Analytics --- Databricks**

An end-to-end demonstration of modern data engineering, analytical
modeling and business intelligence using Databricks.
