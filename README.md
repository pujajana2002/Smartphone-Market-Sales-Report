# Smartphone Market Sales Analysis | Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Project-Portfolio%20Analysis-blue)
![Focus](https://img.shields.io/badge/Focus-Sales%20Analytics-0A7A75)

An interactive Power BI report for exploring smartphone sales performance across brands, mobile models, cities, payment methods, customer ratings, and reporting periods.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Business Objectives](#business-objectives)
- [Dashboard Preview](#dashboard-preview)
- [Report Pages](#report-pages)
- [KPIs and Analysis Areas](#kpis-and-analysis-areas)
- [Data Model and Fields](#data-model-and-fields)
- [Tools and Skills Demonstrated](#tools-and-skills-demonstrated)
- [How to Use the Report](#how-to-use-the-report)
- [Validation Checklist](#validation-checklist)
- [Known Configuration Note](#known-configuration-note)
- [Business Questions to Explore](#business-questions-to-explore)
- [Potential Enhancements](#potential-enhancements)
- [Repository Structure](#repository-structure)
- [Project Information](#project-information)

## Project Overview

The **Smartphone Market Sales Analysis** project uses Power BI to present an interactive view of smartphone sales. The report is organized around four core analytical themes:

1. **Sales performance** – total sales, quantity sold, transactions, and average price.
2. **Product and brand performance** – sales by mobile model and brand.
3. **Customer and payment behaviour** – customer-rating status and payment-method mix.
4. **Time-based performance** – monthly quantity trends, weekday sales, month-to-date (MTD), and comparison with the same period last year.

The report contains three pages: **Dashboard**, **MTD report**, and **same period last year**.

> **Documentation boundary:** This README is based on the supplied Power BI report layout and the dashboard screenshot. The source dataset and the internal Power Query/DAX definitions were not independently available for verification. Therefore, this document describes the report's visible structure and analytical intent; it does not claim unverified cleaning steps, data-source details, or business outcomes.

## Business Objectives

- Monitor overall smartphone sales and transaction activity.
- Compare sales contribution across brands and mobile models.
- Understand the distribution of transactions across payment methods.
- Review customer ratings by rating status.
- Track monthly quantity and day-of-week sales patterns.
- Review month-to-date performance.
- Compare sales with the corresponding period in the previous year.
- Enable users to investigate performance through report filters.

## Dashboard Preview

![Smartphone Market Sales Analysis dashboard](assets/dashboard-preview.png)

*Dashboard screenshot from the supplied Power BI report. The map visual is currently blocked by the local Power BI Desktop security setting; see [Known Configuration Note](#known-configuration-note).*

## Report Pages

### 1. Dashboard

The main dashboard brings together the report's headline metrics and supporting breakdowns.

| Visual | Analytical purpose |
|---|---|
| Total Sales card | Displays the sales total in the current filter context |
| Total Quantity card | Displays the quantity sold |
| Total Transactions card | Displays transaction volume |
| Average Price card | Displays the report's average-price metric |
| Monthly quantity trend | Tracks total quantity by month |
| Customer ratings funnel | Compares rating-status categories |
| Top 3 mobile models | Compares sales for the leading models shown |
| Payment-method donut chart | Shows transaction share by payment method |
| Sales by day name | Compares sales across weekdays |
| Brand summary table | Compares total sales and transactions by brand |
| City map | Intended to show geographic sales distribution |

The page includes slicers for **Mobile Model**, **Payment Method**, and **Brand**, along with month selection.

### 2. MTD Report

The MTD page is designed to review month-to-date performance. It includes KPI cards, a time-based visual, and slicers for mobile model, payment method, and reporting period.

Use this page to investigate how the selected month's performance develops over time. Confirm the exact MTD date-window logic in the DAX measure before using it for formal reporting.

### 3. Same Period Last Year

This page is designed to compare current-period sales with sales from the corresponding period in the previous year. It includes KPI cards, filters, a year/quarter comparison table, and comparison charts.

Use it to investigate year-over-year performance by the available time and product filters. The exact comparison behaviour depends on the DAX measure and calendar-table relationship.

## KPIs and Analysis Areas

The report references the following measures or measure-like fields:

| KPI / field | Intended meaning | Validation required |
|---|---|---|
| `Total_sales` | Total sales value | Confirm source column, aggregation, and currency |
| `total_quantity` | Total quantity sold | Confirm whether this is a sum of units sold |
| `Total_transection` | Transaction count | Confirm whether it counts rows or distinct transaction IDs |
| `Average_price` | Average price metric | Confirm whether this is a simple or weighted average |
| `MTD` | Month-to-date metric | Review date-window logic and calendar relationship |
| `QTD` | Quarter-to-date metric | Review quarter definition and date context |
| `YTD` | Year-to-date metric | Review year definition and date context |
| `Same period last year` | Comparable prior-year metric | Validate date alignment and filter behaviour |

**Important:** The names above follow the report's field naming. The exact DAX expressions were not confirmed from the accessible report layout, so formulas have intentionally not been invented.

## Data Model and Fields

The report layout references a sales table named `Sales_data` and a separate calendar table named `custom_calender`.

### `Sales_data`

Fields visible in the report model include:

- `Brand`
- `City`
- `Customer Age`
- `Customer Name`
- `Customer Ratings`
- `Date`
- `Mobile Model`
- `Payment Method`
- `Price Per Unit`
- `Rating Status`
- `Transaction ID`
- `Units Sold`

The report also references these measure/metric names:

- `Average_price`
- `MTD`
- `QTD`
- `YTD`
- `Same period last year`
- `Total_sales`
- `Total_transection`
- `total_quantity`

### `custom_calender`

The report uses a calendar table for time-based analysis. The visible report uses month, day, year, and quarter analysis.

**Model checks recommended before publishing:**

- Confirm the active relationship between the sales date and calendar date.
- Confirm the calendar contains a continuous date range covering the sales data.
- Confirm the calendar table is marked as a date table if required by the model design.
- Check that month sorting uses a month number rather than alphabetical month names.
- Check that year, quarter, month, and day filters behave consistently across all pages.

## Tools and Skills Demonstrated

Based on the supplied report:

- **Microsoft Power BI Desktop** – report design and interactive visualizations.
- **DAX** – KPI and time-based metrics referenced in the report.
- **Power BI data modeling** – sales and calendar-table structure.
- **Business analysis** – sales, product, payment, customer-rating, and time-period analysis.

Only list **Power Query**, SQL, Excel, Python, or other tools as project technologies if you actually used them in preparing this report.

## How to Use the Report

1. Open `Mobile sales analysis report.pbix` in Power BI Desktop.
2. Start on the **Dashboard** page to review the overall metrics.
3. Use the Mobile Model, Payment Method, Brand, and month filters to focus the analysis.
4. Compare product, payment, rating, and weekday patterns.
5. Open **MTD report** to review month-to-date performance.
6. Open **same period last year** to inspect the prior-year comparison.
7. Reset filters when you want to return to the overall report view.

## Validation Checklist

Before presenting the report as a business decision-making tool, validate the following:

- [ ] Reconcile total sales against the source data.
- [ ] Confirm the transaction-count definition, especially whether `Transaction ID` is distinct-counted.
- [ ] Confirm that quantity uses the correct units field and aggregation.
- [ ] Confirm the average-price formula and currency.
- [ ] Check for blank, misspelled, or inconsistent brand, model, city, and payment-method values.
- [ ] Verify the sales-to-calendar relationship and date coverage.
- [ ] Test MTD, QTD, and YTD calculations at month, quarter, and year boundaries.
- [ ] Test same-period-last-year results against manually selected comparison dates.
- [ ] Confirm slicers affect the intended visuals on each page.
- [ ] Reconcile totals between KPI cards, charts, and tables under the same filters.
- [ ] Confirm geographic fields are correctly categorized before relying on map results.

## Known Configuration Note

In the supplied screenshot, the map visual displays a message that **Map and Filled Map visuals are disabled**. This is a Power BI Desktop security/configuration setting and does not, by itself, indicate that the `City` field or dataset is invalid.

If your organization permits map visuals:

1. In Power BI Desktop, select **File → Options and settings → Options**.
2. Under **Global**, open **Security**.
3. Enable **Use Map and Filled Map visuals**.
4. Select **OK** and restart Power BI Desktop if required.
5. Set the city column's data category to **City**. If reliable latitude and longitude fields exist in the dataset, use them in the corresponding map field wells.

## Business Questions to Explore

The report can be used to investigate questions such as:

1. Which brands contribute the most to total sales?
2. Which mobile models lead in sales value?
3. How does quantity sold vary from month to month?
4. Which payment methods account for the largest share of transactions?
5. How are customer ratings distributed across rating statuses?
6. Which weekdays show the highest and lowest sales?
7. How does month-to-date performance compare across selected periods?
8. How does current-period sales compare with the same period last year?
9. How do brand, model, and payment-method filters change the results?

These are **analysis questions**, not claimed findings. Add verified answers after validating the underlying data and measure definitions.

## Potential Enhancements

- Add year-over-year sales growth and absolute variance measures.
- Add a clearly defined average selling price, including a weighted-average option where appropriate.
- Add brand and model contribution percentages.
- Add drill-through pages for brand, model, and city-level investigation.
- Add report-page tooltips with supporting KPIs.
- Add a data refresh timestamp and data-quality indicators.
- Improve map accuracy with validated geographic fields.
- Document key DAX formulas and the data-refresh process.
- Add a concise executive summary with verified findings and business recommendations.

## Repository Structure

```text
smartphone-market-sales-analysis/
├── README.md
├── Mobile sales analysis report.pbix
└── assets/
    └── dashboard-preview.png
```

## Project Information

- **Project:** Smartphone Market Sales Analysis
- **Platform:** Microsoft Power BI
- **Report pages:** Dashboard | MTD report | Same period last year
- **Author:** [Your Name]
- **LinkedIn:** [Add your LinkedIn profile URL]
- **Portfolio:** [Add your portfolio URL, if available]

---

If you find this project useful, feel free to explore the report and suggest improvements.
