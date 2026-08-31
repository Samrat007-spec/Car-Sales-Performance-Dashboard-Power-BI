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

Dataset feature

Value

Transactions

23,906

Data fields

16

Years covered

2022–2023

Car companies

30

Vehicle models

154

Dealerships

28

Dealer regions

7

Body styles

5

Vehicle colors

3

Source Columns

Field

Description

Car_id

Unique transaction identifier

Date

Date of sale

Customer Name

Customer first name

Gender

Customer gender category

Annual Income

Reported customer annual income

Dealer_Name

Selling dealership

Company

Vehicle manufacturer

Model

Vehicle model

Engine

Engine configuration

Transmission

Automatic or manual transmission

Color

Vehicle color

Price ($)

Transaction selling price

Dealer_No

Dealer reference number

Body Style

Vehicle body type

Phone

Customer phone reference

Dealer_Region

Dealer sales region

Dashboard Structure

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

2. Details

The Details page supports transaction-level investigation. It retains the major KPI cards and slicers while providing a detailed table containing:

Car ID and sale date

Customer and dealership

Company and model

Vehicle color

Selling price

This page allows users to move from summary metrics to the records behind them.

Headline Performance

The latest year in the dataset is 2023.

KPI

2022

2023

YoY change

Total sales

$300.34M

$371.19M

+23.59%

Cars sold

10,645

13,261

+24.57%

Average selling price

$28,214

$27,991

−0.79%

December 2023 Performance

KPI

MTD result

Sales

$54.28M

Cars sold

1,921

Average price

$28,257

The results show that 2023 growth was driven mainly by higher sales volume. Revenue and vehicle count increased strongly, while average selling price decreased slightly.

Selected Business Insights

Company Performance

Chevrolet generated the highest 2023 sales revenue at $27.11M, followed by Ford at $25.43M and Dodge at $25.02M.

Regional Performance

Austin led all dealer regions with $65.04M in 2023 sales from 2,296 vehicles. Janesville ranked second with $58.73M.

Body-Style Performance

SUVs produced the highest 2023 revenue at $99.89M and also had the highest vehicle volume. Hatchbacks ranked second with $82.77M.

Color Performance

Pale White vehicles generated $174.53M, representing the strongest revenue contribution among the three color groups.

Data Preparation

The Excel data was prepared in Power Query before dashboard development. The workflow focused on:

Promoting the first row as column headers.

Assigning correct data types to dates, prices, income, and identifiers.

Reviewing blank and duplicate transaction IDs.

Standardizing text categories used in slicers and visuals.

Creating a calendar table to support time-intelligence calculations.

Building relationships between the calendar and sales transaction tables.

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
