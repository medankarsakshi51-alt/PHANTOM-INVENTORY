# Cloud-Native Advanced Inventory Analytics Pipeline (Snowflake + dbt + Power BI)

## 📌 Project Overview
Welcome to my first industry-standard advanced analytics project! This repository contains the data transformation blueprint for an enterprise-grade **Medallion Architecture** pipeline. 

The project solves a major real-world business challenge: capturing fragmented, messy transactional inventory data and transforming it into clean, automated, and audit-ready business intelligence.

## 🛠️ The Tech Stack Architecture
*   🔌 **Snowflake (The Adapter):** Serves as our centralized cloud data warehouse, handling raw ingestion stages inside `PHANTOM_DB`.
*   ⚙️ **dbt (The Transformer):** Coordinates data modeling transformations, automated testing, and execution tracking.
*   📊 **Power BI (The Visualizer):** Connects to the structured analytical schema to provide automated business insights and exception tracking.

---

## 🏗️ Medallion Pipeline Framework

### 🥉 Bronze Layer (Ingestion)
*   **Location:** `PHANTOM_DB.STAGE`
*   **Tables:** `stg_physical_baselines`, `stg_inbound_receiving`, `stg_pos_sales`
*   **Purpose:** Houses raw, completely immutable source data exactly as it arrives from physical environments.

### 🥈 Silver Layer (Enriched Analytics Logic)
*   **Location:** `PHANTOM_DB.DBT_SMEDANKAR.silver_inventory_reconciliation`
*   **Key Logic:** Resolves data gaps via a **Unified Chronology Timeline Spine**, applies multi-month weight rules, and calculates complex windowed running totals across chronological intervals.

### 🥇 Gold Layer (Analytics-Ready Star Schema)
*   **Location:** `PHANTOM_DB.DBT_SMEDANKAR`
*   **Schema Structure:** Fully normalized Star Schema optimized for high-speed dimensional queries.
*   **Dimensions:** `dim_stores`, `dim_products`, `dim_calendar`
*   **Facts:** `fact_inventory_snapshot` (for variance formulas & anomalies) and `fact_order_lines` (for pricing).

---

## 🚀 Key Takeaways & Analytical Focus
*   **Advanced Analytical Modeling:** Leveraged dbt window functions to calculate point-in-time running stock balances.
*   **Data Integrity Assertions:** Built operational testing assertions inside dbt to flag data anomalies before they impact dashboards.
*   **Semantic Layer Performance:** Modeled fact and dimension boundaries to keep Power BI visual renders exceptionally fast.
