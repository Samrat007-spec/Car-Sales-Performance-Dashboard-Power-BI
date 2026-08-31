Project Summary

This Power BI portfolio project transforms a car dealership sales dataset into an interactive performance dashboard. It gives decision-makers a clear view of sales revenue, vehicle volume, average selling price, year-over-year growth, and performance across companies, dealers, regions, body styles, and colors.

The project demonstrates an end-to-end business intelligence workflow using Excel, Power Query, data modeling, DAX, and Power BI dashboard design.

Business Objective

Automotive sales teams need more than a list of transactions. They need to understand whether sales are improving, which market segments are driving revenue, and where performance requires attention.

This dashboard was designed to answer four business questions:

How are current-year sales performing compared with the previous year?

Which companies, dealerships, and regions generate the most revenue?

Which vehicle attributes—such as body style and color—drive sales?

Which individual transactions contribute to the reported KPIs?

Dataset Overview

The Excel source contains 23,906 transaction records from 2 January 2022 to 31 December 2023.

The Power BI report contains two pages.

1. Overview

The Overview page provides an executive summary through KPI cards and interactive visuals:

YTD total sales, year-over-year difference, growth rate, and MTD sales

YTD average price, year-over-year change, and MTD average price

YTD cars sold, year-over-year change, and MTD vehicle count

Weekly YTD sales trend

Sales distribution by body style and color

Cars sold by dealer region

Company-wise sales performance table

Region, body style, transmission, and engine slicers

Data Model

The report uses a simple analytical model:

Fact table: car_data, containing transaction-level sales records.

Date dimension: Calendar Table, used for weekly, monthly, YTD, and prior-year analysis.

Relationship: Calendar date to transaction date.

This structure keeps the model easy to understand while enabling reliable time-intelligence measures.

Core DAX Measures

The following examples represent the main calculation logic used in the dashboard.

Total Sales

Total Sales =
SUM(car_data[Price ($)])

YTD Total Sales

YTD Total Sales =
TOTALYTD(
    [Total Sales],
    'Calendar Table'[Date]
)

Previous-Year YTD Sales

PYTD Total Sales =
CALCULATE(
    [YTD Total Sales],
    SAMEPERIODLASTYEAR('Calendar Table'[Date])
)

Year-over-Year Sales Growth

YoY Sales Growth =
DIVIDE(
    [YTD Total Sales] - [PYTD Total Sales],
    [PYTD Total Sales],
    0
)

Cars Sold

Cars Sold =
COUNTROWS(car_data)

Average Selling Price

Average Price =
DIVIDE([Total Sales], [Cars Sold], 0)

Interactive Features

Page navigation between Overview and Details

Cross-filtering between charts and tables

Dynamic KPI cards

Conditional KPI colors for positive and negative movement

Slicers for dealer region, body style, transmission, and engine

Weekly trend analysis through the calendar table

Geographic sales exploration with a regional map

Tools and Skills Demonstrated

Microsoft Power BI Desktop

Power Query data preparation

Data modeling and date-table relationships

DAX measures and time intelligence

KPI design and variance analysis

Interactive filters and page navigation

Business storytelling and dashboard layout

Automotive sales analysis

How to Use This Project

Download or clone the repository.

Open dashboard/Car Sales.pbix in Power BI Desktop.

If the source path has changed, update it in Transform data → Data source settings.

Select Refresh to load the Excel data.

Use the slicers and page navigation to explore the dashboard.

Portfolio Value

This project demonstrates the ability to convert raw transactional data into an executive dashboard, define meaningful KPIs, build time-based comparisons, and communicate the drivers behind sales performance.

Disclaimer

This project is intended for learning and portfolio presentation. The dataset does not represent live dealership operations, and the analysis should not be treated as an official business report.
