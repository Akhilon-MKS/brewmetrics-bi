# brewmetrics-bi
BrewMetrics BI  Version-controlled business intelligence solution for BrewMetrics Coffee Co.
# BrewMetrics Business Intelligence

## Project Overview

BrewMetrics Business Intelligence is a Power BI analytics project developed for BrewMetrics Coffee Co. The project analyzes sales transactions across different cities, store formats, product categories, and products.

The objective is to transform the raw sales data into a structured star schema and develop an interactive dashboard that helps explore sales performance, Cold Brew seasonality, city-level performance, and product rankings.

## Objectives

- Analyze overall sales performance.
- Identify seasonal patterns in Cold Brew sales.
- Compare sales performance across cities.
- Analyze product-level sales performance.
- Provide interactive filtering and drill-down analysis.
- Build a version-controlled Power BI project using GitHub.

## Dataset

The project uses the `brewmetrics_sales.csv` dataset.

The dataset contains transaction-level sales information including:

- Date
- City
- Store Format
- Category
- Item
- Quantity
- Unit Price
- Sales Amount

The dataset represents sales across four cities and three store formats.

## Data Model

The project uses a star schema consisting of a central fact table and multiple dimension tables.

### Fact_Sales

`Fact_Sales` contains transaction-level sales information.

Important fields include:

- Sale ID
- Date
- City
- Product
- Store Format
- Quantity
- Unit Price
- Sales Amount

### Dim_Date

`Dim_Date` contains date-related information used for time-based analysis.

It supports:

- Date analysis
- Month analysis
- Time-based calculations
- Month-over-month analysis
- Running totals

### Dim_City

`Dim_City` contains city information used to analyze geographical sales performance.

### Dim_Product

`Dim_Product` contains product information used for product and category analysis.

The dimension tables are connected to the `Fact_Sales` table to support interactive analysis.

## DAX Measures

The project includes the following DAX measures:

### Total Sales

Calculates the total sales amount.

### MoM Growth %

Calculates month-over-month sales growth.

### Running Total Sales

Calculates cumulative sales over time.

### Product Rank

Ranks products based on total sales using `RANKX`.

### Average Transaction Value

Calculates the average sales value per transaction.

## Dashboard

The Power BI dashboard contains multiple interactive visuals.

### KPI Cards

The dashboard displays:

- Total Sales
- Average Transaction Value
- Month-over-Month Growth

### Cold Brew Sales Trend

The dashboard contains a visual for analyzing the sales trend of Cold Brew over time.

### Sales by City

A city-level visual allows comparison of sales performance across the different cities.

### Top Products by Sales

The dashboard ranks products according to their total sales.

### City and Store Format Drill-Down

The dashboard provides a drill-down from City to Store Format to allow more detailed analysis.

### Interactive Slicer

The dashboard includes slicers that allow users to filter the report and explore different parts of the dataset.

## Key Dashboard Insights

### 1. Cold Brew Seasonal Pattern

The Cold Brew sales trend visual allows the seasonal sales pattern of Cold Brew to be explored across the available months.

### 2. City-Level Performance

The city-level sales visual shows differences in sales performance between the four cities.

### 3. Product Performance

The product ranking visual identifies the products contributing the highest sales within the selected dashboard filters.

## Tools Used

- Power BI Desktop
- Power BI Project (.pbip)
- DAX
- Power Query
- Git
- GitHub
- GitHub Copilot
- VS Code

## Project Workflow

The project was developed incrementally using Git version control.

The major stages were:

1. Repository setup
2. Star schema creation
3. DAX measure development
4. Dashboard development
5. Documentation and reflection

## Repository

This project is maintained using Git and GitHub with the complete development history preserved.
