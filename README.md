# Supply Chain Logistics Performance Dashboard (Power BI)
## Project Overview

In this project, I acted as a Business Intelligence Analyst and built an end-to-end Supply Chain Logistics Performance Dashboard in Power BI to solve a real-world logistics analysis scenario.

My objective was to analyse:

- Delivery performance
- Shipment value trends
- Country-level distribution
- Shipment mode efficiency

to support data-driven logistics decision-making.

This project follows a complete BI workflow:

Dataset Selection → Data Preparation → Data Modelling → Dashboard Development → Deployment

## Dataset

I used a real-world supply chain shipment dataset containing:

- Scheduled delivery dates
- Actual delivery dates
- Shipment modes (Air, Air Charter, Truck, Ocean)
- Countries
- Vendors
- Product groups
- Quantity and shipment value

The dataset contains more than 7,000 rows, which allowed me to build a proper analytical data model.

## Part A — Data Preparation (Power Query)

I performed extensive data cleaning and transformation in Power Query.

Key transformations:

- Renamed queries for clarity
- Removed unnecessary columns
- Removed duplicate records
- Fixed incorrect data types
- Handled missing/null values
- Trimmed and standardised text
- Split project codes into meaningful attributes
- Created a Revenue Check (Total Value) derived column
- Extracted Year, Month, and Quarter from date fields

Dimension tables created:

- Dim_Date
- Dim_Country
- Dim_Product
- Dim_ShipmentMode
- Dim_Vendor

Each major table contains more than 10 applied steps, as shown in the Power Query screenshots and Query Dependency view.

## Part B — Data Modelling

I designed a Star Schema to support scalable analytics.

Fact table: 
- Fact_Delivery

Dimension tables:
- Dim_Date
- Dim_Country
- Dim_Product
- Dim_ShipmentMode
- Dim_Vendor

Modelling decisions:

- Configured one-to-many relationships
- Applied single-direction filtering
- Avoided many-to-many relationships
- Hid technical key fields from report view
- Organised the model logically in Model View

This structure improves performance and ensures clean filtering across visuals.

## DAX Calculations

I created the following key measures:
```
Total Deliveries = COUNTROWS(Fact_Delivery)

Total Shipment Value = SUM(Fact_Delivery[Total Value Check])

Total Quantity = SUM(Fact_Delivery[Quantity])

Delivery Days =
DATEDIFF(
    Fact_Delivery[Delivered to Client Date],
    Fact_Delivery[Scheduled Delivery Date],
    DAY
)

Avg Delivery Days = AVERAGE(Fact_Delivery[Delivery Days])

On Time Delivery Rate =
DIVIDE(
    SUM(Fact_Delivery[On Time Delivery]),
    COUNTROWS(Fact_Delivery),
    0
)
```

These measures allow me to monitor volume, value, efficiency, and service performance.

## Part C — Dashboard Development

I designed a single-page executive dashboard with a logical top-down layout.

### KPI Summary:
- Total Deliveries → 10K
- On-Time Delivery Rate → 88.51%
- Total Quantity → 189M
- Total Shipment Value → 45M

These provide a quick operational overview.

### Trend Analysis

Shipment Value Trend by Month
→ Identifies seasonal shipment patterns and performance changes over time.

### Comparative Analysis

Shipment Value by Country
→ Highlights high-value countries and supports regional logistics strategy.

### Distribution Analysis

Shipment Mode Distribution
→ Shows the proportion of shipments by transport mode.

### Performance Analysis

Average Delivery Days by Shipment Mode
→ Identifies the fastest transport modes and those contributing to delays.

### Interactivity

I added slicers for:
- Year
- Country
- Product Group
- Shipment Mode

All visuals are cross-filtered to enable dynamic exploration.

### Design Approach

I used a minimal professional theme:

- Teal → primary logistics metrics
- Yellow → performance indicator (On-Time Delivery Rate)
- Grey → supporting information

This structure supports executive decision-making.

 ### Part D — Deployment

I published the report to Power BI Service, generated a public dashboard link, and confirmed accessibility.

The repository includes screenshots of:

- Dataset sourcing
- Power Query transformations
- Applied steps
- Query dependencies
- Data model relationships
- Dashboard page
- Publishing confirmation

## Key Insights

From the dashboard I observed:

- On-time delivery performance is 88.51%, indicating room for improvement.
- Air transport dominates shipment volume but has higher average delivery days, especially for Air Charter.
- Some shipment modes have significantly higher delivery times.
- Shipment value is concentrated in a few top countries.
- Monthly shipment value shows mid-year peaks.

These insights support route optimisation, mode selection, and regional planning.

## Tools Used

- Power BI Desktop
- Power Query
- DAX
- Star Schema Data Modelling
- Power BI Service

## Repository Structure
dataset/
power-query/
data-model/
dax-measures/
dashboard/
deployment/
report/


👤 Author

Ilham Mohamed

## Result

This project demonstrates a complete end-to-end BI solution, from raw data preparation to analytical modelling, interactive dashboard design, and cloud deployment.