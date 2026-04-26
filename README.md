# Retail Sales Analytics Project using Azure Synapse 

## Project Overview

This project is an end-to-end **Retail Sales Data Analytics** solution that processes raw retail data from Kaggle, transforms it using Medallion Architecture (Bronze → Silver → Gold layers), and visualizes key business insights through an interactive **Power BI Dashboard**. The entire data pipeline is built on **Azure Synapse Analytics**.

The project demonstrates how to:
- Ingest Kaggle retail data into ADLS & Load into SQL Bronze Layer.
- Clean and standardize raw data using T-SQL (Silver Layer).
- Build a business-ready analytics layer (Gold Layer).
- Create a professional Power BI dashboard for retail performance.

---

## Requirements & Analysis Goals

### Business Questions to Answer:

1. **What is the overall business performance?**
   - Total Sales (Revenue)
   - Total Orders
   - Total Items Sold

2. **How is revenue trending over time?**
   - Yearly revenue trends
   - Monthly seasonality patterns

3. **Who are the top customers and stores?**
   - Top 10 customers by spending
   - Store performance and ranking

4. **What are the preferred payment methods?**
   - Distribution of sales by (Cash, Card, Contactless)

### Dashboard Visuals Required:

| Visual Type | View Name | Purpose |
|-------------|-----------|---------|
| **Cards (3)** | `vw_kpis` | Display Total Sales, Total Orders, Total Items Sold |
| **Line Chart** | `vw_revenue_by_year` | Show Sales trend by year |
| **Line Chart** | `vw_monthly_revenue` | Monthly sales trend and seasonality |
| **Donut Chart** | `vw_payment_distribution` | Sales by payment type (Cash/Card/Contactless) |
| **Bar Chart** | `vw_store_performance` | Best selling stores comparison |

---

## Medallion Architecture

This project follows the **Medallion Architecture** (Bronze → Silver → Gold) for data processing:

### Layer Details:

| Layer | Schema | Description |
|-------|--------|-------------|
| **Bronze** | `bronze` | Raw data as-is from Kaggle CSV. Contains dirty data: NULLs, duplicates, and mixed formats. |
| **Silver** | `silver` | Cleaned data. Removed NULLs, fixed negative quantities/prices, and removed duplicates. |
| **Gold** | `gold` | Business-level aggregates and views. Ready for Power BI with pre-calculated KPIs. |

---

## Tools & Technologies Used

| Tool | Purpose |
|------|---------|
| **Azure Synapse Analytics** | Data ingestion, SQL transformation, and analytics |
| **Azure Data Lake Storage (ADLS)** | Raw data storage for Kaggle CSV files |
| **Power BI** | Interactive dashboard and data visualization |
| **T-SQL** | Data cleaning (Silver) and View creation (Gold) |

### Azure Services:
- Azure Synapse Workspace
- Dedicated SQL Pool
- Azure Data Lake Storage Gen2

---

## SQL Views Created (Gold Layer)

```sql
-- Dashboard views
gold.vw_kpis                  -- Cards: Total Sales, Orders, Items Sold
gold.vw_revenue_by_year       -- Line chart: Sales trend by year
gold.vw_monthly_revenue       -- Line chart: Sales trend by month
gold.vw_payment_distribution  -- Donut chart: Sales by payment type
gold.vw_top_customers         -- Bar chart: Top 10 best customers
gold.vw_store_performance      -- Bar chart: Best selling stores
