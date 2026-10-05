🛒 Customer Shopping Behavior Analysis & Interactive Dashboard
A end-to-end data analytics project analyzing customer demographic patterns, purchasing habits, subscription behavior, and product performance. This project integrates Python (Pandas, SQLAlchemy) for Exploratory Data Analysis (EDA) and cleaning, MySQL for relational database querying, Power BI for interactive business intelligence dashboards, and Gamma for executive presentation deck generation.

📌 Project Overview
Understanding customer shopping behavior is critical for modern e-commerce and retail strategy. This project provides actionable business insights by evaluating 3,900 customer transactions across various demographic profiles, product categories, shipping types, and payment methods.

Key Objectives
Data Ingestion & Cleaning: Standardize raw transactional data, handle missing values, and engineer business-relevant features using Python.
Database Integration: Automate data pipeline loading from Python into a MySQL relational database.
Advanced SQL Analysis: Formulate complex SQL queries (CTEs, Window Functions, Case Statements) to extract customer behavior trends.
Interactive Visualization: Design an executive-ready Power BI dashboard with key performance indicators (KPIs) and interactive filters.
Stakeholder Communication: Deliver data-driven insights through an executive report and a Gamma presentation deck.
📊 Dataset Overview
Source File: customer_shopping_behavior.csv
Total Records: 3,900 customer records
Total Attributes: 18 raw columns (13 categorical, 4 numerical, 1 float)
Primary Features
Demographics: Customer ID, Age, Gender, Location
Transactional Data: Item Purchased, Category (Clothing, Accessories, Footwear, Outerwear), Purchase Amount (USD), Season, Size, Color
Customer Behavior: Review Rating, Subscription Status (Yes/No), Previous Purchases, Frequency of Purchases, Payment Method
Promotions & Fulfillment: Shipping Type, Discount Applied, Promo Code Used
🛠️ Tools & Technologies Used
Stage	Tools / Libraries	Purpose
Data Ingestion & EDA	Python, Jupyter Notebook, Pandas, NumPy	Exploratory analysis, data cleaning, and feature engineering
Database & ETL	MySQL Workbench, SQLAlchemy, PyMySQL	Automated DB pipeline loading and relational schema setup
Querying & Analytics	MySQL (SQL)	Advanced querying, customer segmentation, window functions, CTEs
Business Intelligence	Power BI Desktop	Interactive dashboard creation, DAX measures, slicers, visual analytics
Presentation & Reporting	Gamma App, Markdown / PDF	AI-generated slide presentation and executive summary report
🔄 Project Execution Workflow
Raw CSV Dataset
      │
      ▼
Python (Pandas) ──► EDA, Missing Value Imputation, Feature Engineering
      │
      ▼
SQLAlchemy ETL ──► Automated Pipeline to MySQL Database (`pythonconnectivity`)
      │
      ▼
MySQL Queries ──► Customer Segmentation, CTEs, Window Functions, Business KPIs
      │
      ▼
Power BI ────────► Interactive Dashboard (KPIs, Category Revenue, Subscription Metrics)
      │
      ▼
Gamma / Report ──► Executive Stakeholder Presentation & Summary
Step 1: Data Cleaning & Feature Engineering (Python)
Missing Value Imputation: Handled 37 missing values in Review Rating by imputing the median rating grouped by product Category.
Schema Standardization: Cleaned column headers to lowercase snake_case (e.g., Purchase Amount (USD) $\rightarrow$ purchase_amount).
Redundancy Cleanup: Validated that discount_applied and promo_code_used were 100% identical and dropped the duplicate column.
Feature Engineering:
Age Segmentation (age_group): Grouped customer age into 4 quantiles: Young, Adult, Middle_aged, and Senior.
Purchase Frequency Mapping (frequency_purchases): Converted text frequencies (Weekly, Fortnightly, Monthly, Annually) into numeric day equivalents (7, 14, 30, 365).
Step 2: Database Connectivity & SQL Pipeline
Established an automated database connection using sqlalchemy.create_engine() and pymysql.
Streamlined data export directly from Pandas DataFrame to MySQL table (customer) in database pythonconnectivity.
Step 3: SQL Data Analysis (10 Core Business Queries)
Ran 10 structured SQL queries in MySQL Workbench to answer key business questions:

Revenue by Gender: Calculated total spend for Male vs. Female shoppers.
High-Value Discount Users: Identified customers using discounts while spending above average purchase amount ($59.76).
Top Rated Products: Ranked top 5 products by average review rating.
Fulfillment Comparison: Compared average transaction amounts between Standard and Express shipping.
Subscription Impact: Evaluated average spend and total revenue between subscribers vs. non-subscribers.
Discount Rates by Item: Identified top 5 products with highest discount application percentage using conditional aggregation.
Customer Loyalty Segmentation: Classified shoppers into New (1 purchase), Returning (2–10 purchases), and Loyal (>10 purchases) using CASE statements.
Top Products per Category: Used Window Functions (ROW_NUMBER() OVER (PARTITION BY category ORDER BY total_orders DESC)) and CTEs to extract top 3 items in each category.
Repeat Buyer Subscriptions: Measured subscription conversion rates among repeat buyers (>5 previous purchases).
Demographic Revenue Contribution: Calculated total revenue generated by each age_group.
📈 Power BI Dashboard Highlights
The interactive Power BI dashboard is structured for executive monitoring with real-time dynamic filtering.

Key Performance Indicators (KPIs)
Total Customers: 3.9K
Average Spend per Transaction: $59.76
Average Review Rating: 3.75 / 5.0
Primary Dashboard Visuals
Revenue by Product Category: Bar chart highlighting sales distribution across Clothing, Accessories, Footwear, and Outerwear.
Subscription Breakdown: Donut chart displaying subscriber distribution (27% Yes vs 73% No).
Revenue by Payment Method: Breakdown of total sales across Credit Card, PayPal, Venmo, Cash, etc.
Age Group Analytics: Dual bar charts displaying total purchase amount and customer count across Young, Adult, Middle_aged, and Senior.
Interactive Slicers: Dynamic slicers for Gender, Category, Shipping Type, and Subscription Status.
💡 Key Results & Business Insights
Overall Revenue & Basket Size:
Total customer base of 3,900 customers with an average spend of $59.76 per order.
Subscription Opportunity:
Only 27% of customers are enrolled in the subscription program, representing a major growth opportunity for loyalty marketing and recurring revenue incentives.
Product Category Dominance:
Clothing and Accessories drive the highest volume and overall revenue contribution compared to Outerwear and Footwear.
Demographic Trends:
Sales are well-distributed across age brackets, with Middle_aged and Adult segments driving strong consistent volume.
Fulfillment & Discounts:
High usage of discounts across key product lines without degrading average order value, indicating strong promo code elasticity.
💻 How to Run & Replicate This Project
Prerequisites
Python 3.9+ (with Jupyter Notebook or JupyterLab)
MySQL Server & MySQL Workbench
Power BI Desktop
Setup Instructions
Clone the Repository:

git clone https://github.com/your-username/customer-shopping-behavior-analysis.git
cd customer-shopping-behavior-analysis
Install Python Dependencies:

pip install pandas sqlalchemy pymysql notebook
Run EDA & Data Cleaning Script:

Open and execute Customer_Shopping_behaviour_EDA.ipynb in Jupyter Notebook.
Ensure your local MySQL credentials (root:admin@localhost) match the connection parameters in cell [20].
Execution will clean the raw CSV and auto-populate the table customer in database pythonconnectivity.
Execute SQL Queries:

Open MySQL Workbench and connect to your instance.
Load and execute Data_Analysis_SQL_Queries.sql to run the 10 business analysis queries.
Open Power BI Dashboard:

Launch Power BI Desktop and open PowerBI_Dashboard.pbix.
Update the MySQL data source settings if prompted, or refresh the connection to view updated visuals.
📄 License & Acknowledgments
Dataset: Customer Shopping Behavior Dataset
Author: Data Analytics Portfolio Project
License: MIT License

