# 🛍️ Customer Shopping Behavior Analysis & Interactive Dashboard

An end-to-end **Data Analytics project** analyzing **3,900 customer transactions** to understand customer demographics, purchasing behavior, product performance, subscription adoption, discounts, and revenue trends.

The project follows a complete analytics workflow:

**Python → MySQL → SQL Analysis → Power BI → Business Insights**

---

## 📌 Project Overview

In e-commerce, understanding **who customers are, what they purchase, how frequently they purchase, and what influences their spending** is essential for making better business decisions.

This project analyzes customer shopping data to answer practical business questions such as:

* Which product categories generate the most revenue?
* Do subscribers spend more than non-subscribers?
* Which customers are New, Returning, or Loyal?
* Which products perform best within each category?
* Where are discounts being used most frequently?
* Which age groups contribute the most revenue?
* How does shipping type affect average purchase value?
* What is the subscription conversion rate among repeat buyers?

The analysis combines **Python for data preparation and EDA, MySQL for structured business analysis, and Power BI for interactive visualization and reporting.**

---

# 🎯 Business Objectives

### Customer Analysis

Understand customer demographics, purchasing frequency, previous purchases, and customer loyalty.

### Revenue Analysis

Identify major revenue contributors across product categories, demographics, gender, and payment methods.

### Product Analysis

Identify top-performing products and compare product performance across categories.

### Subscription Analysis

Evaluate subscriber behavior and identify opportunities to increase subscription adoption.

### Promotion Analysis

Understand discount usage and identify products with high discount application rates.

### Business Decision Support

Convert data findings into actionable recommendations for marketing, customer retention, promotions, and subscription growth.

---

# 🛠️ Tools & Technologies

| Area                | Tools                 | Purpose                                        |
| ------------------- | --------------------- | ---------------------------------------------- |
| Data Cleaning & EDA | Python, Pandas, NumPy | Data preparation, exploration & transformation |
| Notebook            | Jupyter Notebook      | Reproducible analysis                          |
| Database            | MySQL                 | Structured data storage                        |
| ETL                 | SQLAlchemy, PyMySQL   | Python-to-MySQL data pipeline                  |
| Data Analysis       | SQL                   | Business questions & customer segmentation     |
| Visualization       | Power BI              | Interactive dashboard & KPI analysis           |
| Reporting           | Gamma, Markdown, PDF  | Executive presentation & reporting             |

---

# 📊 Dataset Overview

**Dataset:** Customer Shopping Behavior Dataset

* **Records:** 3,900
* **Raw Columns:** 18
* **Domain:** E-commerce / Retail

### Key Features

**Customer Demographics**

* Customer ID
* Age
* Gender
* Location

**Transaction Details**

* Item Purchased
* Category
* Purchase Amount (USD)
* Season
* Size
* Color

**Customer Behavior**

* Review Rating
* Subscription Status
* Previous Purchases
* Frequency of Purchases
* Payment Method

**Promotion & Fulfillment**

* Discount Applied
* Promo Code Used
* Shipping Type

---

# 🔄 Project Workflow

```text
                    Raw CSV Dataset
                           │
                           ▼
                    Python / Pandas
                           │
             ┌─────────────┴─────────────┐
             │                           │
        Data Cleaning                 EDA
             │                           │
             └─────────────┬─────────────┘
                           │
                  Feature Engineering
                           │
                           ▼
                  SQLAlchemy + PyMySQL
                           │
                           ▼
                     MySQL Database
                           │
                           ▼
                   SQL Business Analysis
                           │
                           ├── CTEs
                           ├── CASE Statements
                           ├── Window Functions
                           └── Customer Segmentation
                           │
                           ▼
                       Power BI
                           │
                  Interactive Dashboard
                           │
                           ▼
                  Business Insights
                           │
                           ▼
              Executive Report / Presentation
```

---

# 🧹 1. Data Cleaning & Feature Engineering — Python

Python and Pandas were used to prepare the raw dataset for analysis.

## Missing Value Treatment

The dataset contained **37 missing values in `review_rating`**.

Instead of removing these records, missing ratings were imputed using the **median rating within the respective product category**.

This helped preserve the available customer records while accounting for category-level differences.

---

## Column Standardization

Column names were converted into a consistent **lowercase snake_case** format.

For example:

```text
Purchase Amount (USD)
        ↓
purchase_amount
```

This made the dataset easier to work with in Python, SQL, and Power BI.

---

## Redundant Data Removal

`discount_applied` and `promo_code_used` were found to contain identical information.

The redundant field was removed to avoid duplication and simplify downstream analysis.

---

## Feature Engineering

### Age Group

Customers were grouped into four age segments:

* Young
* Adult
* Middle_aged
* Senior

### Purchase Frequency

Text-based purchase frequencies were converted into approximate day equivalents:

| Frequency   | Equivalent Days |
| ----------- | --------------: |
| Weekly      |               7 |
| Fortnightly |              14 |
| Monthly     |              30 |
| Annually    |             365 |

These engineered features were later used for segmentation and business analysis.

---

# 🗄️ 2. Database Integration — MySQL

The cleaned dataset was loaded into MySQL using **SQLAlchemy and PyMySQL**.

### Database Structure

```text
Database: pythonconnectivity
Table: customer
```

### ETL Flow

```text
CSV
 ↓
Pandas DataFrame
 ↓
Data Cleaning & Transformation
 ↓
SQLAlchemy
 ↓
MySQL
```

This created a simple and reproducible Python-to-MySQL data pipeline.

---

# 🔎 3. SQL Business Analysis

After loading the data into MySQL, I developed **10 business-focused SQL analyses**.

## Business Questions Answered

### 1️⃣ Revenue by Gender

Compared total customer spending across male and female shoppers.

### 2️⃣ High-Value Discount Users

Identified customers who used discounts while spending above the overall average purchase amount.

**Average purchase amount: $59.76**

### 3️⃣ Top-Rated Products

Identified the top 5 products based on average customer review rating.

### 4️⃣ Shipping Type Analysis

Compared average purchase amounts between:

* Standard Shipping
* Express Shipping

### 5️⃣ Subscription Impact

Compared subscribers and non-subscribers based on:

* Average purchase amount
* Total revenue

### 6️⃣ Discount Usage by Product

Identified products with the highest percentage of discount application using conditional aggregation.

### 7️⃣ Customer Loyalty Segmentation

Customers were classified into:

| Segment   | Previous Purchases |
| --------- | -----------------: |
| New       |                  1 |
| Returning |               2–10 |
| Loyal     |                >10 |

### 8️⃣ Top Products Within Each Category

Used **CTEs and Window Functions** to identify the top 3 products in each category.

Example:

```sql
ROW_NUMBER() OVER (
    PARTITION BY category
    ORDER BY total_orders DESC
)
```

### 9️⃣ Repeat Buyer Subscription Analysis

Measured subscription adoption among customers with more than 5 previous purchases.

### 🔟 Revenue by Age Group

Compared revenue contribution across Young, Adult, Middle_aged, and Senior customers.

---

# 📈 4. Power BI Dashboard

The cleaned and analyzed data was used to create an interactive Power BI dashboard for business monitoring and exploration.

## 📌 Key KPIs

| KPI                           |    Value |
| ----------------------------- | -------: |
| Total Customers               |     3.9K |
| Average Spend per Transaction |   $59.76 |
| Average Review Rating         | 3.75 / 5 |

---

## Dashboard Components

### 💰 Revenue by Product Category

Analyzes revenue contribution from:

* Clothing
* Accessories
* Footwear
* Outerwear

### 👥 Subscription Analysis

Shows the distribution between:

* Subscribers — **27%**
* Non-subscribers — **73%**

### 💳 Payment Method Analysis

Analyzes sales across different payment methods such as:

* Credit Card
* PayPal
* Venmo
* Cash

### 👤 Age Group Analysis

Compares customer count and purchase amount across different age groups.

### 🎛️ Interactive Slicers

The dashboard allows users to filter the analysis by:

* Gender
* Category
* Shipping Type
* Subscription Status

---

# 💡 Key Business Insights

## 1. Subscription Adoption Is a Growth Opportunity

Only **27% of customers are subscribed**, while 73% are not.

### Recommendation

The business could test:

* Targeted subscription offers
* Loyalty rewards
* Exclusive subscriber benefits
* Personalized promotions
* Repeat-purchase incentives

---

## 2. Clothing & Accessories Are Major Sales Contributors

Clothing and Accessories show strong sales contribution compared with the other product categories.

### Recommendation

The business could focus on:

* Cross-selling
* Product bundles
* Personalized recommendations
* Seasonal campaigns

---

## 3. Customer Loyalty Can Be Used for Targeted Marketing

Segmenting customers into **New, Returning, and Loyal** groups enables different marketing strategies.

For example:

```text
New Customers
      ↓
First-purchase incentive

Returning Customers
      ↓
Personalized offers

Loyal Customers
      ↓
VIP / Loyalty Rewards
```

---

## 4. Discount Strategy Can Be Optimized

Discount usage is significant across several products.

Rather than applying discounts uniformly, the business can evaluate promotions based on:

* Customer segment
* Product category
* Purchase frequency
* Previous purchases
* Customer value

This can help improve promotional efficiency.

---

# 📊 Dashboard Preview

> **Add your actual Power BI screenshot here.**

```markdown
![Power BI Dashboard](images/powerbi_dashboard.png)
```

You can also add screenshots of:

* Python EDA
* MySQL query results
* Power BI dashboard
* Executive presentation

---

# 📁 Project Structure

```text
customer-shopping-behavior-analysis/
│
├── data/
│   └── customer_shopping_behavior.csv
│
├── notebooks/
│   └── Customer_Shopping_behaviour_EDA.ipynb
│
├── sql/
│   └── Data_Analysis_SQL_Queries.sql
│
├── powerbi/
│   └── PowerBI_Dashboard.pbix
│
├── presentation/
│   └── Customer_Shopping_Behavior_Presentation.pdf
│
├── images/
│   └── powerbi_dashboard.png
│
└── README.md
```

> Update the folder/file names above to match your actual GitHub repository structure.

---

# 🚀 How to Run the Project

## Prerequisites

Install:

* Python 3.9+
* Jupyter Notebook / JupyterLab
* MySQL Server
* MySQL Workbench
* Power BI Desktop

---

## 1. Clone the Repository

```bash
git clone https://github.com/your-username/customer-shopping-behavior-analysis.git

cd customer-shopping-behavior-analysis
```

---

## 2. Install Dependencies

```bash
pip install pandas numpy sqlalchemy pymysql notebook
```

---

## 3. Run the Python Notebook

Open:

```text
Customer_Shopping_behaviour_EDA.ipynb
```

Run the notebook to:

1. Load the raw CSV
2. Explore the dataset
3. Handle missing values
4. Standardize column names
5. Remove redundant fields
6. Create engineered features
7. Connect to MySQL
8. Load the cleaned data into the database

### ⚠️ Database Configuration

Before running the MySQL connection code, update your own:

* Host
* Username
* Password
* Port
* Database name

---

## 4. Run SQL Analysis

Open:

```
Data_Analysis_SQL_Queries.sql
```

Connect to MySQL using MySQL Workbench and execute the queries.

---

## 5. Open Power BI Dashboard

Open:

```
PowerBI_Dashboard.pbix
```

If prompted, update the MySQL data source credentials and refresh the data.

---

# 📚 Skills Demonstrated

### Python

* Pandas
* NumPy
* Data Cleaning
* Exploratory Data Analysis
* Feature Engineering
* Data Transformation

### SQL

* Aggregations
* GROUP BY
* CASE Statements
* Conditional Aggregation
* CTEs
* Window Functions
* Ranking
* Customer Segmentation

### MySQL

* Database Integration
* Table Creation
* Data Loading
* Relational Analysis

### Power BI

* KPI Design
* DAX Measures
* Interactive Dashboards
* Slicers
* Data Visualization
* Business Reporting

### Business Analytics

* Revenue Analysis
* Customer Segmentation
* Product Performance
* Subscription Analysis
* Promotion Analysis
* Demographic Analysis
* Insight Generation
* Business Recommendations

---

# 🧠 Key Learning

This project helped strengthen my understanding of the complete **Data Analytics lifecycle**.

The most important learning was that analytics is not simply:

> **Clean data → Create dashboard**

A strong analyst starts with the **business problem**:

```text
Business Question
       ↓
What data do I need?
       ↓
Clean & Validate
       ↓
Analyze
       ↓
Identify Patterns
       ↓
Generate Insight
       ↓
Understand Business Impact
       ↓
Recommend Action
```

This project helped me practice connecting **technical analysis with business decision-making**.

---

# 🔮 Future Improvements

Potential extensions include:

* RFM customer segmentation
* Customer Lifetime Value (CLV)
* Customer churn analysis
* Sales forecasting
* Cohort analysis
* Product recommendation analysis
* Customer-level profitability
* Predictive modeling
* Automated dashboard refresh

---

# 📄 Dataset & Acknowledgment

**Dataset:** Customer Shopping Behavior Dataset

This project was created for **learning, portfolio development, and demonstrating practical Data Analytics skills**.

---

# 👩‍💻 Author

## Amrita Kumari

**Data Analyst | Python | SQL | Power BI | Excel**

[LinkedIn](https://www.linkedin.com/in/amrita-k-id555/)

---



