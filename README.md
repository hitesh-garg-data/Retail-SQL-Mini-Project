**📊 Retail SQL Mini Project**

Retail sales analysis using SQL (SQLite) to explore profitability, aggregation logic, and metric validation on a small dataset.
It includes KPI validation, product-level insights, monthly performance, region trends, and identification of loss-making items.

**🔧 Tools & Technologies**

SQLite / DB Browser for SQLite

SQL (Aggregations, Grouping, HAVING, String Manipulation)

Excel (for quick validation)

Markdown for documentation

## 📁 Repository Structure


Retail-SQL-Mini-Project/
│
├── retail_sql_project/
│ ├── Retail_Mini_Project_SQL.db
│ ├── Retail_Mini_Project_SQL.csv
│ ├── Retail_Mini_Project_SQL.sqbpro
│ ├── Readme_Retail_Mini_Project.md ← Full detailed query-by-query explanation
│ └── screenshots/
│ ├── Dataset_validation.png
│ ├── Monthly_sales.png
│ ├── Region_wise_performance.png
│ ├── Top_products.png
│ ├── Products_negative_profit.png
│ └── Top10_units.png
│
└── README.md ← (this file)

---
**🧠 Project Overview**

The goal of this project is to apply SQL to analyze retail sales data and validate profitability logic across products, regions, and time.

Key business questions answered include:

Which products generate the highest revenue?

Which months perform best or worst?

Which regions drive sales—and are they profitable?

Which products consistently lose money?

Are profit calculations internally consistent?

**📸 Key Output Screenshots**
1️⃣ Dataset Validation

Confirms Profit = Net Sales – Cost across entire dataset.
(See /screenshots/Dataset_validation.png)

2️⃣ Monthly Sales & Profit

Shows monthly revenue trend and identifies weak/strong months.
(See /screenshots/Monthly_sales.png)

3️⃣ Regional Performance

Compares revenue, units sold, and profit margin across regions.
(See /screenshots/Region_wise_performance.png)

4️⃣ Top Revenue-Generating Products

(See /screenshots/Top_products.png)

5️⃣ Negative-Profit Products

(See /screenshots/Products_negative_profit.png)

6️⃣ Top 10 Products by Units Sold

(See /screenshots/Top10_units.png)

**🧠 Observations & Patterns**

📦 Products

Ball is the #1 product by both revenue and units sold.

Glue Stick, Water Bottle, and Notebook generate negative total profit.

Not all high-volume items are profitable — pricing or cost may need correction.

📅 Monthly Trends

February: Only loss-making month (₹112K sales but –₹14K profit).

March: Highest sales and profit month (₹176K sales, ₹40K profit).

Overall quarterly pattern: January → drop in February → strong rebound in March.

🌎 Regional Performance

North: Highest revenue + profit.

East: Good sales but weak margins.

South: Lowest profit margin across regions.

West: Smallest region but stable margins.

✔ Dataset Validation

Total Profit perfectly matches Net Sales – Cost.

No structural data quality issues found in key numeric fields.

**📂 Full Query-by-Query Breakdown**

The complete SQL queries (with explanations + insights) are inside:

📄 retail_sql_project/Readme_Retail_Mini_Project.md

This includes:

Query 1 → Top Products by Revenue

Query 2 → Monthly Sales

Query 3 → Region-wise Performance

Query 4 → Negative-Profit Products

Query 5 → Top 10 by Units Sold

Query 6 → Dataset Validation

🚀 How to Run This Project

Download Retail_Mini_Project_SQL.db from retail_sql_project/data/

Open it in DB Browser for SQLite

Copy SQL queries from Readme_Retail_Mini_Project.md

Execute & compare with screenshots

**👤 Author**

Hitesh Garg  
Finance & Business Data Analyst

|Portfolio: https://www.notion.so/Portfolio-Hitesh-Garg-Data-Analytics-Journey-2a9e7a66bd4380e1904acef1d5f325d3
