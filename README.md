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
  - [Data Enrichment Examples](#data-enrichment-examples)
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

Note
- The dataset is provided in Excel format (.xlsx), making it easy to import into Excel for cleaning, enrichment, and analysis.
- Orders are linked to Customers and Products via Customer ID and Product ID, forming a simple relational structure suitable for lookups and dashboarding.

## Data Preparation
Before building the dashboard, the raw Excel data was cleaned, standardized, and enriched to ensure accuracy and consistency.
### Cleaning Steps & Examples
- Duplicate Removal:
  - Checked for duplicate Order ID and Customer ID entries.
  - Removed any repeated rows to avoid inflating sales metrics.
- Standardizing Dates:
  - Converted Order Date to DD-MMM-YYYY format.
  - Ensured all pivot tables and charts interpret dates consistently.
- Numeric Conversion:
  - Converted Unit Price and Sales columns to numeric format for calculations and aggregation.
  - Removed any currency symbols or text artifacts.
- Text Standardization:
  - Roast types standardized to Light / Medium / Dark.
  - Sizes standardized to 250g, 0.5kg, 1kg.
  - Loyalty card values set consistently to Yes / No.
- Calculated Fields:
  - Sales = Quantity × Unit Price

    - =Quantity * Unit_Price

  - Loyalty Segmentation:

    - =IF(Loyalty_Card="Yes","Loyalty","Non-Loyalty")

  - Enriched order data with customer and product attributes:
    - XLOOKUP → Pull Customer Name, Email, Country
    - INDEX + MATCH → Pull Coffee Type, Roast Type, Size

### Data Enrichment Example
- Customer Lookup:

  - =XLOOKUP([@Customer_ID], Customers[Customer_ID], Customers[Customer_Name])

- Product Attribute Lookup (Roast Type example):

  - INDEX(Products[Roast_Type], MATCH([@Product_ID], Products[Product_ID], 0))

### Quality Checks
- Verified no missing values for critical columns (Order ID, Customer ID, Product ID, Sales).
- Validated lookup accuracy by sampling random rows and confirming XLOOKUP and INDEX-MATCH results matched source sheets.
- Ensured categorical values matched dashboard slicers for correct filtering (e.g., Roast Type, Size, Loyalty Card).

## Excel Analysis
The cleaned and enriched dataset enabled the creation of pivot tables, charts, and interactive filters to answer key business questions. Each question was addressed using Excel formulas, XLOOKUP, INDEX-MATCH, IF statements, and pivot tables.

- Business Questions Answered
  - How have total coffee sales trended over time?
    - Created a PivotTable with Order Date in rows (grouped by month/quarter/year) and Sales in values.
    - Visualized trends using a line chart with a timeline slicer for interactive filtering.
  - Which countries contribute the most to overall coffee sales?
    - PivotTable: Country in rows, Sales in values.
    - Displayed as a bar chart for quick comparison and filtered by slicers (Roast, Size, Loyalty).
  - Who are the top 5 customers by total sales value?
    - PivotTable: Customer Name in rows, Sales in values.
    - Sorted descending by sales and filtered to Top 5.
    - Visualized with a bar chart for easy identification of high-value customers.
  - Which coffee roast type generates the highest sales revenue?
    - PivotTable: Roast Type in rows, Sales in values.
    - Combined with slicer filters to view trends by date, size, or loyalty segment.
  - How does coffee size (250g, 0.5kg, 1kg) influence sales volume and revenue?
    - PivotTable: Size in rows, Sales and Quantity in values.
    - Charts showed revenue share by size, highlighting the most popular packaging.
  - What impact does the loyalty card program have on sales?
    - PivotTable: Loyalty Card in rows, Sales and Quantity in values.
    - Compared averages using an IF formula to segment loyalty vs non-loyalty customers:

      - =IF([@Loyalty_Card]="Yes", Sales, 0)

    - Revealed that loyalty card members spend more on average.
  - Which coffee types are most popular among customers?
    - PivotTable: Coffee Type in rows, Sales in values.
    - Charted the distribution to identify top-selling coffee types (Arabica, Robusta, etc.).
  - Are certain roast types or sizes more popular in specific countries?
    - PivotTable: Country in rows, Roast Type / Size in columns, Sales in values.
    - Enabled cross-country comparison using slicers to drill down by date or loyalty status.

- Analysis Approach
  - All PivotTables were connected to interactive slicers (Timeline, Roast Type, Size, Loyalty Card) to allow dynamic exploration.
  - Calculated fields and helper columns ensured sales metrics were correctly segmented.
  - Charts were formatted consistently to highlight trends and key insights.













