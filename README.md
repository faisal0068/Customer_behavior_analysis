🛍️ Customer Shopping Behavior Analysis
An end-to-end data analysis project examining retail customer shopping patterns using Python, SQL (PostgreSQL), and Power BI. The project covers data cleaning, exploratory analysis, business querying, and an interactive dashboard.

📌 Business Problem
A leading retail company wants to better understand its customers' shopping behavior to improve sales, customer satisfaction, and long-term loyalty. Management has noticed changes in purchasing patterns across demographics, product categories, and sales channels.

"How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?"


📁 Project Structure
customer-behavior-analysis/
│
├── customer_shopping_behavior.csv          # Raw dataset
├── Customer_behavior_data_cleaning.ipynb   # Python: data cleaning & EDA
├── Customer_behavior_analysis.sql          # SQL: business queries (Q1–Q10)
├── Customer_behavior_Dashboard.pbix        # Power BI dashboard
└── README.md

🗂️ Dataset Overview
FieldDetailsSourceRetail customer transactionsRecords3,900 rowsFeatures18 columns (17 after cleaning)Age Range18 – 70 yearsCategoriesClothing, Footwear, Outerwear, AccessoriesSeasonsWinter, Spring, Summer, FallPayment MethodsCredit Card, Cash, PayPal, Venmo, Bank Transfer, Debit CardPurchase Range$20 – $100 USD
Key columns: Customer ID, Age, Gender, Item Purchased, Category, Purchase Amount (USD), Season, Review Rating, Subscription Status, Shipping Type, Discount Applied, Previous Purchases, Payment Method, Frequency of Purchases

🐍 Python — Data Cleaning & EDA
File: Customer_behavior_data_cleaning.ipynb
Steps performed:

Data Loading — Loaded CSV using pandas, inspected shape, dtypes, and summary stats
Missing Value Treatment — 37 nulls in Review Rating imputed using category-level median
Column Standardisation — Renamed all columns to lowercase with underscores; renamed purchase_amount_(usd) → purchase_amount
Feature Engineering: Age Group — Created age_group column using pd.qcut() with 4 bins: Young Adult, Adult, Middle-aged, Senior
Feature Engineering: Purchase Frequency (Days) — Mapped frequency text values to numeric days (e.g. Weekly → 7, Monthly → 30)
Duplicate Column Removal — Dropped promo_code_used (fully identical to discount_applied)
Export to PostgreSQL — Loaded cleaned DataFrame into a customer table using SQLAlchemy + psycopg2

Libraries: pandas, sqlalchemy, psycopg2

🗄️ SQL — Business Analysis
File: Customer_behavior_analysis.sql
Database: PostgreSQL — table: customer
#QuestionConcepts UsedQ1Total revenue by genderSUM, GROUP BYQ2Discount users above average spendSubquery, AVGQ3Top 5 products by average review ratingAVG, ROUND, ORDER BY, LIMITQ4Standard vs. Express shipping spendAVG, WHERE IN, GROUP BYQ5Subscriber vs. non-subscriber spendAVG, SUM, GROUP BYQ6Top 5 products by discount rateCASE, SUM, ROUND, ORDER BYQ7Customer segmentation (New / Returning / Loyal)CTE, CASE, COUNTQ8Top 3 products per categoryCTE, ROW_NUMBER(), PARTITION BYQ9Repeat buyers and subscription likelihoodWHERE, COUNT, GROUP BYQ10Revenue contribution by age groupSUM, GROUP BY, ORDER BY

📊 Power BI Dashboard
File: Customer_behavior_Dashboard.pbix
The interactive dashboard provides a self-service view of customer shopping behaviour for business stakeholders. Slicers allow filtering by Gender, Season, Category, and Subscription Status.
Visuals included:

Revenue by Gender
Revenue by Product Category
Revenue by Season
Top Products by Review Rating
Shipping Type vs. Average Spend
Subscriber vs. Non-Subscriber Revenue
Payment Method Distribution
Revenue by Age Group


💡 Key Business Recommendations

Targeted Discounts — Discounted customers still outspend average; deploy targeted campaigns for high-intent segments
Subscription Expansion — Subscribers show higher spend; invest in onboarding and subscriber-exclusive perks
Product Prioritisation — Feature top-rated products in homepage placements and recommendation engines
Seasonal Planning — Align inventory and promotions with seasonal purchase peaks
Gender-Specific Marketing — Tailor campaigns and category emphasis per gender segment
Shipping Upsell — A/B test Express shipping upgrade prompts at checkout for high-value carts


🛠️ Tools & Technologies
ToolVersionPurposePython3.xData cleaning & EDAPandasLatestData manipulationSQLAlchemy + psycopg2LatestPostgreSQL connectionPostgreSQLLatestBusiness query analysisPower BI DesktopLatestDashboard & visualisationJupyter NotebookLatestInteractive Python environment

🚀 How to Run
1. Python Notebook
bash# Install dependencies
pip install pandas sqlalchemy psycopg2-binary

# Open the notebook
jupyter notebook Customer_behavior_data_cleaning.ipynb
2. SQL Queries
bash# Connect to PostgreSQL and run
psql -U postgres -d customer_behavior -f Customer_behavior_analysis.sql

Make sure the Python notebook has been run first to load the customer table into PostgreSQL.

3. Power BI Dashboard

Open Customer_behavior_Dashboard.pbix in Power BI Desktop
Refresh the data source if needed to point to your local PostgreSQL instance


👤 Author
Faisal Khan
M.Sc. Data Science — University of Mumbai
LinkedIn · GitHub
