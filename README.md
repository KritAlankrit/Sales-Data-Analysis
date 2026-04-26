# Retail Store Profitability & Sales Analysis (Power BI)

## Project Overview
This project is an end-to-end Power BI data analytics solution designed to extract, transform, and visualize store sales data. The primary objective is to empower stakeholders to track KPIs, compare period-over-period performance, and identify the most (and least) profitable products across multiple regions.

## Business Objectives
The dashboard was built to answer the following core business analytics questions:
1. What are the **Top and Bottom 5** products by Sales, Profit, and Quantity Sold?
2. How do **sales trends** vary over time (daily, monthly, quarterly, annually)?
3. What is the mathematical relationship between Net Sales and Profit?
4. **Custom Period Analysis:** How do Sales, Profit, and Quantity compare between *any two arbitrary dates* selected by the user?
5. What is the average discount offered within each promotion category?
6. What is the **Total Number of Orders** processed?
7. How are sales distributed geographically across different cities?
8. Can users drill down into granular, transaction-level details (Sales, Profit, Discount, Net Sales) using dynamic filtering?

## Data Engineering & ETL Processing (Power Query / M Code)
Before visualization, the raw data (`Store+Data.xlsx`) underwent rigorous ETL processing using Power Query to ensure high data quality and accuracy:
- **Data Modeling:** Designed a robust **Star Schema** with dimension tables (`Dim Customers`, `Dim Product`, `Dim Promotion`) mapping to a central Fact Table. Implemented completely disconnected date tables (`Date Table 1`, `Date Table 2`) to enable advanced side-by-side DAX period comparisons.
- **Data Cleansing:** Promoted headers, enforced strict data typing (Int64, Date, Text) to prevent downstream DAX errors, and securely handled nulls (replaced with 0) to prevent broken aggregations.
- **Feature Engineering & Transformation:**
  - Executed Left Outer Joins to securely map relational `Price Per Unit` and dynamic `Promotion Percentages` into historical transaction records.
  - Engineered custom logic for `Total Sales` (Units × Price) and derived exact `Discount Values`.
  - Formulated precision mathematical logic for `Net Sales` (Total - Discount) and a scaled 10% `Profit` margin.
  - Generated a unique `Order ID` index column serving as a primary surrogate key for unique line-item tracking.

## Dashboard Pages & Insights

1. **Sales Analysis:** High-level executive view featuring the `Total Orders` KPI (3,510), time-series trends tracking sales volume, and a Geospatial Map highlighting heavy sales concentrations in major Indian cities.

   <img width="1373" height="788" alt="image" src="https://github.com/user-attachments/assets/e0f3b7ed-3bfc-4577-aae6-e4563225a668" />

2. **Date Comparison:** An advanced reporting page utilizing two parallel date slicers, allowing end-users to uniquely compare custom historical periods side-by-side across Sales, Profit, and Quantity.

   <img width="1372" height="773" alt="image" src="https://github.com/user-attachments/assets/6d3a77fe-9018-4965-94c5-472753f5df9a" />

3. **Top/Bottom Analysis:** Diagnostic bar charts rapidly isolating core business drivers (e.g., iPhone 14 dominating top sales vs. hygiene products lagging).

   <img width="1376" height="774" alt="image" src="https://github.com/user-attachments/assets/f075dd94-8580-4691-b25b-514f2e5e8000" />  

4. **Discount Analysis:** Evaluates the aggregate impact of marketing campaigns, revealing 'Weekend Flash Sales' yielding the highest average discount value at 22.6K.

   <img width="1378" height="775" alt="image" src="https://github.com/user-attachments/assets/293ad620-5581-4403-9d26-b9a784620365" />

5. **Profit vs Sales:** A scatter plot map displaying the strict 10% profit margin correlation across transactional revenue clusters.

   <img width="1375" height="773" alt="image" src="https://github.com/user-attachments/assets/f7f66402-d094-44ce-9fe4-1dc3e1ed26f2" />

6. **Detailed Matrix:** A high-granularity lookup table enabling users to drill down into individual Order IDs, dynamically filterable by Customer, Product, Date, and Promotion type.

   <img width="1375" height="771" alt="image" src="https://github.com/user-attachments/assets/1656dda7-657b-4eb0-be2c-8ee5055a1793" />

## How to Run Locally
1. Clone this repository.
2. Ensure you have [Power BI Desktop](https://powerbi.microsoft.com/desktop/) installed.
3. Open `Proj_1.pbix` to interact with the dashboard.
