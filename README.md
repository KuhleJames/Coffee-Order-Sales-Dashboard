# Coffee-Order-Sales-Dashboard

![Image Failed to Load](assets/images/Churn_Analysis_Image.png)


# Table of contents

- [Project Overview](#project-overview)
  - [Executive Summary](#executive-summary)
  - [Business Problem](#business-problem)
  - [Project Objective](#project-objective)
  - [Key Metrics & KPIs](#keymetrics-&-kpi)
- [Tools & Workflow](#tools-&-workflow)
- [Data Collection](#data-collection)
  - [Source](#source)
  - [Structure & Format](#structure-&-format)
- [Data Preparation](#data-preparation)
  - [Cleaning Steps & Examples](#cleaning-steps-&-examples)
  - [Quality Checks](#Quality-Checks)
- [Excel Analysis—How each business question was answered](#excel-analysis-how-each-business-question-was-answered)
- [Advanced Formulas & Calculations](#advanced-formulas-&-calculations)
  - [Excel formulas (examples)](#excel-formulas-(examples))
- [Dashboard Design](#dashboard-design) 
  - [Layout & Visuals](#layout-&-visuals)
  - [User Interaction & Features](#user-interaction-&-features)
- [Key Insights & Recommendations](#key-insights-&-recommendations)
  - [Trends Identified](#trends-identified)
  - [Recommendations](#recommendations)
 
# Project Overview
## Executive Summary
This project transforms a fragmented set of transaction, customer and product spreadsheets into a single, interactive Excel dashboard that answers the core business questions about coffee sales: what sells, where, to whom, and when. 

The dashboard allows business users to explore sales trends over time, compare performance by roast type and size, measure loyalty-card impact, see geographic distribution, and identify the highest-value customers, all using Excel tools (PivotTables, slicers, and formulas). The output supports rapid, data-driven decisions for marketing, product management and customer success teams.
## Business Problem
Prior to this project the coffee business relied on static, manual spreadsheets for reporting. The pain points were:
- No single source of truth for sales aggregated across orders, customers and products.
- Insufficient visibility into temporal trends (seasonality, growth).
- Hard to compare sales across countries, roast types, and package sizes quickly.
- No simple way to evaluate loyalty card effectiveness or to identify top customers for retention/upsell.
- Manual reporting took considerable time and was error-prone.

Those issues limited the ability to run targeted promotions, allocate inventory, or prioritise customer outreach.
## Project Objective
Deliver a repeatable, documented Excel-based analysis and dashboard that:
- Consolidates Orders, Customers and Products into a consistent dataset.
- Answers the 8 core business questions (trend, geography, roast, size, loyalty, top customers, coffee type, cross-country preferences).
- Presents an interactive dashboard (timeline slicer, roast/size/loyalty slicers, charts).
- Provides documented formulas and reproducible steps for others to follow and extend.
- Produces actionable recommendations and a hand-off path to scale (Power BI / SQL) if needed.

## Key Metrics & KPIs
Below are the core KPIs used in the dashboard and how to compute them:
- Sales Over Time — Total sales by month/quarter/year
- Sales by Geography — Revenue contribution by country
- Top Customers — Sales ranking of top 5 customers
- Roast Type Performance — Revenue share by roast type
- Size Preference — Revenue contribution by product size
- Loyalty Program Impact — Average spend and sales share from loyalty card holders
- Coffee Type Demand — Sales distribution by coffee type
- Customer Retention Potential — Repeat purchases among top customers

## Tools & Workflow
This project was completed entirely in Microsoft Excel, following a structured process that combined data cleaning, enrichment, analysis, and dashboard design, all within a single, reproducible workflow.
Data Cleaning & Preparation
- Imported raw data from three Excel sheets: Orders, Customers, and Products.
- Cleaned the dataset by removing duplicates, correcting data types, and standardizing text entries (e.g., roast type, size).
- Ensured consistent date formats and converted unit prices and sales values to numeric form.
- Added a calculated Sales column using:

=Quantity * Unit_Price

Data Enrichment
- Merged information across sheets using lookup functions:
  - XLOOKUP to retrieve customer details (name, email, country) and loyalty card members.
  - INDEX + MATCH to pull product attributes (coffee type, roast type, size).
  - IF to extract coffee type name and roast type name from product attributes.
Analysis & Aggregation
- Built PivotTables to summarise key metrics such as total sales, sales by country, roast type performance, and top customers.
- Applied calculated fields within PivotTables to compare different segments (e.g., loyalty vs. non-loyalty spend).
- Tested calculations using filtered tables to ensure accuracy and consistency.
Dashboard Development
- Designed an interactive Excel dashboard combining:
  - Line charts for total sales over time.
  - Bar charts for country and top customers.
  - Slicers for Roast Type Name, Size, and Loyalty Card.
- Aligned charts for visual balance and optimised color contrast for readability.
- Ensured slicers dynamically update all visuals, allowing users to explore insights seamlessly.
Documentation & Workflow Traceability
- Each step, from raw data cleaning to final dashboard, was documented within the Excel workbook (separate tabs labeled Raw Data, Cleaned Data, Dashboard).
- The GitHub repository includes the final Excel file, documentation, and step-by-step notes to allow others to reproduce the results.

## Data Collection
### Source
The dataset for this project comes from a YouTube tutorial by Mo Chen, which provides fictional coffee sales data for learning purposes. The data simulates real-world coffee transactions, including customer details, product attributes, and order history, allowing us to build an end-to-end dashboard scenario.
### Structure & Format
The data is organised into three separate Excel sheets, each serving a distinct role in the analysis:

Orders — Transactional data cpturing each sale:

| Column | Description |
| --- | --- | 
| Order ID | Unit identifier for each order |
| Order Date | Date of the transaction |
| Customer ID | Unique identifier linking to customer details |
| Product ID | Unique identifier linking to product details |
| Quantity | Number of units purchased |
| Customer Name | Pulled via XLOOKUP |
| Email | Pulled via XLOOKUP |
| Country | Pulled via XLOOKUP |
| Coffee Type | Pulled via INDEX-MATCH |
| Roast Type | Pulled via INDEX-MATCH |
| Size | Pulled via INDEX-MATCH |
| Unit Price | charges |
| Sales | Price per unit |
| Coffe Type Name | Pulled via IF |
| Roast Type Name | Pulled via IF |
| Loyalty Card | Pulled via XLOOKUP |

Customers — Customer information:

| Column | Description |
| --- | --- | 
| Customer ID | Unique identifier |
| Customer Name | Full name |
| Email | Contact email |
| Phone Number | Optional |
| Address Line 1 | Street address |
| City | City |
| Country | Country of residence |
| Postcode | Postal Code |
| Loyalty Card | Yes/No indicator for loyalty program |

Products — Product details:

| Column | Description |
| --- | --- | 
| Product ID | Unique identifier |
| Cofee Type | Arabica, Robusta, Excelsa, Liberica |
| Roast Type | Lihgt, Medium, Dark |
| Size | 250 g, 0.5 kg, 1 kg |
| Unit Price| Price per unit |
| Price per 100 g | Calculated metric |
| Profit | Profit per unit |





