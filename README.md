# Consolidated FMCG Data Pipeline using Databricks Lakehouse

## Project Overview

This project demonstrates an **end-to-end Data Engineering pipeline** built using **Databricks Lakehouse architecture** for a real-world **FMCG retail consolidation use case**.

In this scenario, **Atliqon**, a large FMCG retail enterprise, acquires a smaller retail company (**Sports-Bar**) along with plans to onboard more regional retailers in the future.  
Atliqon already operates a mature **Gold-layer Lakehouse**, and the objective of this project is to **seamlessly integrate and streamline incoming data from newly acquired companies into the parent organization’s analytics ecosystem**.

The pipeline is designed to:
- Process the **newly acquired company’s data independently**
- Align it with Atliqon’s existing data model
- Continuously enrich and merge it into Atliqon’s analytics-ready Gold layer
- Power **business dashboards and insights** without disrupting existing systems

---

## Business Problem

Retail mergers often fail at the data layer due to:
- Inconsistent schemas
- Different pricing and product structures
- Fragmented customer and order data
- Manual and error-prone integrations

This project solves that by implementing a **scalable, modular ELT pipeline** that:
- Handles **new acquisitions independently**
- Standardizes and cleans incoming data
- Merges it with enterprise-grade analytics tables
- Supports **continuous data ingestion and enrichment**

---

## 🏗️ Architecture Approach

The project follows **Databricks Medallion Architecture**:

### 🟤 Bronze Layer
- Raw ingestion of Sports-Bar retail data
- No transformations applied
- Acts as a historical and auditable source

### ⚪ Silver Layer
- Data cleaning and standardization
- Schema alignment with Atliqon’s data model
- Dimension-level processing (customers, products, pricing)

### 🟡 Gold Layer
- Business-ready fact and dimension tables
- Enriched views combining:
  - Atliqon’s existing Gold data
  - Sports-Bar’s processed data
- Optimized for analytics and dashboards

---


---

## Data Flow Summary

1. **Atliqon Gold Layer already exists**
2. Sports-Bar data is ingested independently
3. Dimensions are processed and standardized
4. Fact data is loaded (full + incremental)
5. Enriched view (`vw_fact_orders_enriched`) merges:
   - Parent company data
   - Newly acquired company data
6. Dashboards consume only the enriched Gold view

This design ensures **minimal coupling** and **maximum scalability** for future acquisitions.

---

## 📊 Analytics & Dashboarding

- Built using **Databricks SQL Dashboards**
- AI-assisted query generation using **Databricks Genie**
- Single-page executive dashboard showing:
  - Revenue & order KPIs
  - Market-wise performance
  - Order status distribution
  - Trend and growth analysis

Dashboards are powered entirely from the **Gold layer view**, ensuring consistency and performance.

---

## Technologies Used

| Category | Tools |
|-------|------|
| Data Processing | Apache Spark (PySpark) |
| Data Platform | Databricks (Free Edition) |
| Storage | Amazon S3 |
| Architecture | Medallion (Bronze, Silver, Gold) |
| Languages | Python, SQL |
| Analytics | Databricks SQL |
| Visualization | Databricks Dashboards |
| AI Assistance | Databricks Genie |
| Version Control | GitHub |

---

## Design Highlights

- Modular pipeline design for easy onboarding of new companies
- Separation of setup, dimension, and fact processing
- Support for **incremental data loads**
- Reusable utilities and standardized schemas
- Analytics layer isolated from ingestion logic
- Production-style folder and execution ordering

---

## What This Project Demonstrates

- Real-world **data engineering problem-solving**
- Handling **enterprise-scale data consolidation**
- Applying **Lakehouse architecture in practice**
- Designing pipelines that scale with business growth
- Building analytics-ready systems, not just ELT jobs

---

## Future Enhancements

- Onboard additional acquired retailers
- Introduce streaming i

<img width="510" height="750" alt="Screenshot 2026-02-05 001949" src="https://github.com/user-attachments/assets/79fb75b5-3e14-407f-8dad-aa577098c71d" />






                    ┌──────────────────────────┐
                    │     Source Systems       │
                    │                          │
                    │  • Sports-Bar Retail     │
                    │  • Future Acquisitions   │
                    └─────────────┬────────────┘
                                  │
                                  ▼
                     ┌─────────────────────────┐
                     │       Bronze Layer       │
                     │   Raw Data Ingestion     │
                     │   (Unprocessed Data)     │
                     └─────────────┬───────────┘
                                   │
                                   ▼
                     ┌─────────────────────────┐
                     │       Silver Layer       │
                     │  Data Cleaning &         │
                     │  Standardization         │
                     │                          │
                     │  • Customers             │
                     │  • Products              │
                     │  • Pricing               │
                     └─────────────┬───────────┘
                                   │
                                   ▼
        ┌────────────────────────────────────────────────┐
        │                  Gold Layer                    │
        │  Business-Ready Fact & Dimension Tables        │
        │                                                │
        │  • Existing Atliqon Gold Data                  │
        │  • Newly Integrated Sports-Bar Data            │
        └─────────────┬──────────────────────────────────┘
                      │
                      ▼
        ┌────────────────────────────────────────────────┐
        │        Enriched Analytics View                  │
        │        vw_fact_orders_enriched                  │
        └─────────────┬──────────────────────────────────┘
                      │
                      ▼
        ┌────────────────────────────────────────────────┐
        │        Databricks SQL Dashboard                 │
        │        FMCG Business Insights                   │
        └────────────────────────────────────────────────┘


## 📊 FMCG Analytics Dashboard

> Built using Databricks SQL Dashboards and powered by the Gold-layer view.

![FMCG DashBoard](https://github.com/user-attachments/assets/c9ad9a66-5caa-4d0b-ab42-bc62bd8cf784)


