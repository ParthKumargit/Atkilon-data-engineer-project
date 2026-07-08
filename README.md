# FMCG End-to-End Data Engineering Pipeline on Databricks
---

## 📖 Project Overview

**Atkilon** (the acquiring company) has a mature, structured data system, while **Sports Bar** (the acquired startup) has unstructured, inconsistent data. After the acquisition, the challenge is to integrate both companies' data into one unified, scalable analytics platform.

This project builds that pipeline from scratch using the **Medallion Architecture** (Bronze → Silver → Gold), producing clean, BI-ready datasets for reporting and natural-language querying.

### Business Problem
- Two companies, two very different data systems.
- Inconsistent formats, schemas, and data quality between the merged entities.
- Need for a single source of truth to support unified reporting and decision-making post-acquisition.

---

## 🏗️ Architecture

```
 Raw Data (Atlon + Sports Bar)
        │
        ▼
 ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
 │   Bronze    │ --> │   Silver    │ --> │    Gold     │
 │ (Raw Ingest)│     │ (Cleaned &  │     │ (Aggregated/│
 │             │     │  Conformed) │     │  Business-  │
 │             │     │             │     │   Ready)    │
 └─────────────┘     └─────────────┘     └─────────────┘
        │                                       │
        ▼                                       ▼
   Amazon S3                          BI Dashboard / Genie
  (Data Lake Storage)                (Natural Language Q&A)
```

- **Bronze Layer** – Raw data ingested as-is from both companies, no transformations.
- **Silver Layer** – Cleaned, deduplicated, standardized, and conformed to a common schema.
- **Gold Layer** – Business-level aggregates, dimensional models, and curated tables ready for reporting.

---

## 🛠️ Tech Stack

| Category            | Tools / Technologies              |
|---------------------|------------------------------------|
| Compute Platform     | Databricks (Free Edition)         |
| Languages            | Python, SQL, PySpark               |
| Storage              | Amazon S3 (Data Lake)              |
| Architecture Pattern | Medallion Architecture (Bronze/Silver/Gold) |
| Processing Engine    | Apache Spark                       |
| Reporting            | BI Dashboard                       |
| Natural Language Q&A | Databricks Genie                   |

---

## 📁 Repository Structure

```
.
├── notebooks/
│   ├── 01_bronze_ingestion.py       # Raw ingestion from source systems
│   ├── 02_silver_transformation.py  # Cleaning, standardization, joins
│   ├── 03_gold_aggregation.py       # Business-level aggregates & marts
│   └── 04_genie_setup.py            # Genie space / natural language setup
├── data/
│   ├── atlon/                       # Sample structured source data
│   └── sports_bar/                  # Sample unstructured source data
├── docs/
│   └── architecture_diagram.png
├── dashboard/
│   └── fmcg_dashboard.pbix          # or link to hosted dashboard
├── requirements.txt
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- A free [Databricks](https://www.databricks.com/try-databricks) account (Free Edition)
- An AWS account with an S3 bucket (or adapt to your preferred cloud storage)
- Basic familiarity with Python, SQL, and Spark

---

## 📊 Output

- Unified, query-ready Gold tables combining Atlon and Sports Bar data
- BI dashboard visualizing consolidated FMCG business metrics
- Genie space for natural-language data exploration

---

## 📌 Key Learnings

- Designing a Medallion Architecture for merging heterogeneous data sources
- Handling schema drift and data quality issues from an unstructured source
- Building scalable ETL pipelines with PySpark on Databricks
- Serving business users via BI dashboards and conversational analytics (Genie)
