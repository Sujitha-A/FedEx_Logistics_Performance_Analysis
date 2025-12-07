The README content I provided earlier was already in Markdown format. You can directly save that content into a file named README.md. Here it is again, for your convenience:

# FedEx Logistics Performance Analysis

## Overview
This project, "FedEx Logistics Performance Analysis," is an Exploratory Data Analysis (EDA) focused on optimizing FedEx's global supply chain. It aims to analyze logistics processes, identify bottlenecks, streamline delivery timelines, and reduce freight costs, ultimately enhancing customer satisfaction.

## Dataset Description

The dataset, `SCMS_Delivery_History_Dataset.csv`, provides an in-depth look at FedEx's logistics operations. It includes information on:
- **Transactional Identifiers**: ID, Project Code, PQ #, PO / SO #, ASN/DN #.
- **Geographical & Management**: Country, Managed By, Fulfill Via.
- **Shipping Details**: Vendor INCO Term, Shipment Mode, Weight (Kilograms), Freight Cost (USD), Line Item Insurance (USD).
- **Dates**: PQ First Sent to Client Date, PO Sent to Vendor Date, Scheduled Delivery Date, Delivered to Client Date, Delivery Recorded Date.
- **Product Information**: Product Group, Sub Classification, Vendor, Item Description, Molecule/Test Type, Brand, Dosage, Dosage Form, Unit of Measure (Per Pack), Line Item Quantity, Line Item Value, Pack Price, Unit Price, Manufacturing Site, First Line Designation.

**Initial State**: The raw dataset comprised 10324 entries and 33 columns. It had missing values in 'Shipment Mode', 'Dosage', and 'Line Item Insurance (USD)'. Several columns, particularly 'Weight (Kilograms)' and 'Freight Cost (USD)', contained non-numeric string values referring to other IDs, and date columns were stored as 'object' types.

**Data Wrangling & Cleaning**: Key steps included:
- Handling missing values: Dropped rows with null 'Shipment Mode', imputed 'Line Item Insurance (USD)' with 0.0, and imputed 'Weight (Kilograms)' with median values per 'Product Group'.
- Converting data types: Date columns were converted to datetime objects, and 'Weight (Kilograms)' and 'Freight Cost (USD)' were converted to numeric types after extracting referenced values.
- Addressing inconsistencies: Invalid date combinations and 'Date Not Captured'/'Pre-PQ Process' values in date columns were handled or removed.
- Feature Engineering: New columns like 'Delivery Delay(days)', 'Total Cost', 'Shipment Year', and 'Shipment Rate' were created.

## Business Objective

1.  **Efficient Streamlining** of supply chain operations.
2.  **Improving delivery timelines**.
3.  **Reducing costs** for both the company and its customers.

## Key Questions Explored

Through various visualizations and analyses, the project explored:
- Which countries receive the highest shipment volumes?
- What is the global distribution of shipment modes, and how does it vary in top-performing countries?
- How do different shipment modes (Air, Ocean, Truck, Air Charter) impact the shipment rate (cost per line item) over time?
- Is there a correlation between shipment weight and freight cost across different shipment modes?
- What are the most frequently used Vendor INCO Terms, and how do they influence average delivery delays?
- What are the patterns of delivery delays (early vs. late) across different destination countries?
- How do different shipment modes contribute to delivery delays over the years?
- How efficient are various vendors in terms of lead time (PQ to PO) and promised delivery time (PO to Scheduled Delivery Date), and what are their average delivery delays?
- Which product groups and sub-classifications are most commonly shipped directly from vendors?
- How do fulfillment methods ('Direct Drop' vs. 'From RDC') affect delivery timeliness over the years?
- Which management offices oversee the majority of the shipments?
- How does insurance cost vary by product group, both on average and in total contributions?
- What are the correlation strengths between various numerical features in the dataset?
- How do Delivery Delay, Weight, Freight Cost, and Total Cost interrelate?

## Tools & Libraries Used

- **pandas**: For robust data manipulation, cleaning, and analysis.
- **numpy**: Essential for efficient numerical computations and array operations.
- **matplotlib.pyplot**: Used for static data visualization and plot customization.
- **seaborn**: For creating appealing and informative statistical graphics.
- **plotly.express**: For generating interactive and dynamic plots, particularly scatter plots.
- **matplotlib.gridspec**: For managing subplot layouts in complex visualizations.
- **datetime, timedelta**: For precise handling and calculation of dates and time differences.
- **re**: Utilized for advanced string pattern matching and extraction, especially for cleaning data like 'Weight (Kilograms)' and 'Freight Cost (USD)' columns.

## Visualizations Included

1.  Bar Plot: Shipment Volume by Country.
2.  Pie Charts: Global and Country-specific Shipment Mode Distribution.
3.  Line Plot: Cost of Shipments over Time (Shipment Rate per Line Item).
4.  Interactive Scatter Plot: Freight Charge vs. Shipment Weight, colored by Shipment Mode.
5.  Bar Plot: Frequency of use of Vendor INCO Terms.
6.  Bar Plot: Influence of Vendor INCO Terms on Mean Delivery Delay.
7.  Scatter Plot: Delivery Delay (days) by Country, with dot size indicating count.
8.  Bar Plot: Mean Delivery Delay per Country (showing both positive and negative delays).
9.  Interactive Scatter Plot: Delivery Delay vs. Scheduled Delivery Date, colored by Shipment Mode.
10. Stacked Bar Chart: Supply Chain Time Gaps (PQ to PO, PO to Schedule Date) with Vendors.
11. Bar Plot: Delivery Delay by Vendor.
12. Bar Plot: Product Groups Directly Shipped from Vendors.
13. Line Plot: Time Delay w.r.t. Fulfill Way of the Shipment (comparing 'Direct Drop' and 'From RDC').
14. Count Plot: Distribution of Shipments by 'Managed By' office.
15. Bar Plots: Average and Total 'Line Item Insurance (USD)' by Product Group.
16. Heatmap: Correlation Heatmap of Numerical Features.
17. Pair Plot: Relationships between 'Delivery Delay(days)', 'Weight (Kilograms)', 'Freight Cost (USD)', and 'Total Cost'.

## Production-Grade Features

This project adheres to guidelines emphasizing production-grade readiness, with:
- **Well-structured, formatted, and commented code**: Every significant code block is commented to explain its purpose and logic.
- **Deployment Ready Code**: The entire Jupyter Notebook is designed to be executable in one go without errors, ensuring reproducibility and reliability.
- **Basic Exception Handling**: Implemented during dataset loading to gracefully handle potential file access issues.

## Recommendations

To achieve the business objectives, FedEx should:

1.  **Streamline Supply Chain Operations**:
    - Standardize and monitor time gaps across the entire supply chain to ensure consistent performance.
    - Diversify shipment management responsibilities beyond PMO-US to reduce load and improve localized efficiency.
    - Categorize vendors by their historical performance in lead times and delivery punctuality to select optimal partners.

2.  **Improve Delivery Timelines**:
    - Strictly manage delivery schedules to minimize delays, aiming for on-time or slightly early deliveries, especially for critical items.
    - Implement automated systems for dynamic scheduling and smart assignment of shipment modes based on real-time factors and estimated delivery times.
    - Invest in optimizing transportation networks, particularly for modes like Truck shipments which show higher variability in delays.

3.  **Reduce Costs & Enhance Customer Satisfaction**:
    - Prioritize cost-effective shipment modes (Ocean, Truck) when feasible for a given route and delivery requirement.
    - For urgent or high-value shipments, offer premium air transport options with transparent higher freight costs and associated insurance, ensuring guaranteed on-time delivery.
    - Strategically populate Regional Distribution Centers (RDCs) with high-demand and efficient products to leverage the proven efficiency of RDC-based fulfillment. Less frequently ordered items can continue with direct vendor shipments to avoid storage costs and potential expiry.
    - Explore advertising insurance options for product groups with lower current uptake to increase revenue and protect against losses.

## Project Structure

The project notebook is organized into the following logical sections:

-   **1. Know Your Data**: Initial data inspection, including loading, viewing samples, checking dimensions, data types, duplicates, and missing values.
-   **2. Understanding Your Variables**: Detailed examination of each column, descriptive statistics, and identification of unique values and initial insights.
-   **3. Data Wrangling**: Comprehensive data cleaning, handling of invalid entries, data type conversions, and the creation of new, analytically useful features.
-   **4. Data Visualization, Storytelling & Experimenting with charts**: Extensive Exploratory Data Analysis (EDA) phase, where various plots and charts are generated to uncover patterns, relationships, and anomalies within the data.
-   **5. Solution to Business Objective**: Strategic recommendations and actionable insights derived directly from the EDA to address the initial business objectives.
-   **Further Analysis & Conclusion**: Outlines potential next steps for analysis and summarizes the overall findings and their business implications.
