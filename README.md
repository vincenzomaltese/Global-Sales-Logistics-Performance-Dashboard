# Global Sales & Logistics Performance Dashboard

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT) [![Powered by Power BI](https://img.shields.io/badge/Powered%20by-Power%20BI-yellow?style=for-the-badge&logo=powerbi)](https://powerbi.microsoft.com/)

## Project Overview

This project presents a comprehensive Power BI dashboard designed to provide actionable insights into global sales performance and shipment logistics. It serves as a centralized hub for monitoring key performance indicators (KPIs), analyzing trends, and identifying areas for strategic improvement across different regions, product categories, and sales teams. Built with a focus on clarity and interactivity, this dashboard empowers business stakeholders (from executives to sales managers and logistics coordinators) to make data-driven decisions effectively.

---

## Dashboard Highlights & Key Features

![Dashboard Screenshot](link_to_your_dashboard_image.png) 

The interactive dashboard provides a multi-faceted view of business operations:

1.  **Executive KPI Summary:**
    *   **Total Revenue:** Overall sales performance ($2M).
    *   **Total Shipments:** Volume of shipments processed (5K).
    *   **Shipment Status Breakdown:** Real-time view of Active (2K / 32.78%), Completed (3K / 62.26%), and Returned (248 / 4.96%) shipments.
    *   **Average Delivery Time:** Key logistics efficiency metric (10 days).

2.  **Trend Analysis:**
    *   **Shipments Over Time:** Monthly visualization of shipment volumes segmented by status (Active, Completed, Returned), with an option to toggle to a yearly view.
    *   **Revenue Over Time:** Monthly trend analysis of generated revenue, highlighting seasonality and growth patterns.

3.  **Performance Segmentation:**
    *   **Revenue by Category:** Donut chart illustrating the contribution of each product category (Electronics, Audio, Computing, Office Equipment) to the total revenue.
    *   **Average Delivery Time by Country:** Comparative analysis of logistics performance across different countries, enhanced with conditional formatting (`Perfect`, `Fine`, `Too Long`) to quickly identify potential bottlenecks or efficient regions.
    *   **Sales Person Performance:** Detailed table showcasing individual salesperson contributions, including total shipments managed and their breakdown by status (Active, Completed, Returned).

4.  **Interactivity & Filtering:**
    *   **Dynamic Slicers:** Users can easily filter the entire report by Date Range, Product Category, and Country for targeted analysis.
    *   **Cross-Filtering:** Selecting elements within visuals (e.g., clicking a category or country) dynamically filters other visuals on the page, enabling deeper exploration.

---

## Data Model & Architecture

The foundation of this report is a well-structured data model optimized for performance and analytical flexibility within Power BI, adhering to star schema principles:

*   **Fact Table:**
    *   `Shipment`: Central table containing transactional records, including `Date`, `Delivered On`, `Delivery Time`, `Sales`, `Shipment ID`, and foreign keys (`Product`, `Sales Person`, `Geography`).

*   **Dimension Tables:**
    *   `Product`: Provides details about products (`Product`, `Category`, `Cost per Box`).
    *   `SalesPerson`: Contains information about the sales team (`Sales Person`, `Team`, `Picture`).
    *   `Country`: Holds geographical data (`Geography`, `Region`).
    *   `Calendar`: A standard date dimension table (`Date`, `Month`, `Monthnum`, `Qtr`, `Weekday`) enabling robust time intelligence analysis.

*   **Supporting Tables:**
    *   `All Measures`: A dedicated table (best practice) to house all DAX measures, promoting organization and maintainability.
    *   `Parameter`: Likely utilized for enhancing report interactivity, potentially through Field Parameters (allowing dynamic axis/value selection) or What-if scenarios.

*   **Relationships:** One-to-many relationships are established from dimension tables to the fact table, ensuring data integrity and efficient filtering propagation.

![Data Model Schema](link_to_your_data_model_image.png) // **Nota:** Dovrai caricare l'immagine del modello dati su GitHub e sostituire `link_to_your_data_model_image.png` con il link effettivo.

---

## Key Measures & Calculations (DAX)

The insights presented in the dashboard are driven by powerful Data Analysis Expressions (DAX) measures. While the specific code is embedded within the `.pbix` file, key calculations include:

*   **Core Aggregations:** `SUM` (for Revenue), `COUNTROWS` / `DISTINCTCOUNT` (for Shipments).
*   **Status-Based Calculations:** Using `CALCULATE` to filter shipment counts and percentages based on their status (Active, Completed, Returned).
    *   *Example Concept:* `% Active Shipments = DIVIDE( [Active Shipments Count], [Total Shipments Count] )`
*   **Average Calculation:** `AVERAGE` for determining the Average Delivery Time.
*   **Time Intelligence:** DAX time intelligence functions are leveraged for generating monthly and yearly trends (e.g., `TOTALMTD`, `SAMEPERIODLASTYEAR`, although specific functions depend on the exact trend comparison needs).
*   **Conditional Logic:** Measures likely use `IF` or `SWITCH` functions to categorize Average Delivery Time into performance bands (`Perfect`, `Fine`, `Too Long`) for conditional formatting.

---

## How to View & Interact with the Report

1.  **Prerequisites:** Ensure you have Microsoft Power BI Desktop installed.
2.  **Open the Report:** Download and open the `.pbix` file (`YourProjectFileName.pbix`). // **Nota:** Sostituisci `YourProjectFileName.pbix` con il nome effettivo del tuo file.
3.  **Interact:** Utilize the slicers on the left pane to filter the data. Click on elements within visuals (bars, slices, table rows) to cross-filter the report. Toggle between 'Month' and 'Year' views on the Shipments chart. Hover over data points for tooltips containing specific values.

---
