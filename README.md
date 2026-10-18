# Customer Churn Analysis & Retention Insights

## Project Overview

Customer Churn Analysis & Retention Insights is a data analytics project developed using Python, Pandas, NumPy, SQL, SQLite, Matplotlib, and Seaborn. The project investigates customer attrition by combining customer demographics, subscription details, and customer support information to understand churn patterns and identify customer segments that may require retention attention.

The analysis uses three primary data tables: **Customer, Subscription, and Support**. These tables are imported from an Excel workbook, stored in an SQLite database, and loaded into Pandas DataFrames for data preparation and analysis. The customer table contains 500 records; the final number of unique customers and merged records should be validated after joining the tables.

## Data Cleaning and Preparation

The project includes data cleaning and standardization across all three tables. In the Customer table, the `name` column is renamed to `customer_name`, unnecessary columns such as `interests` and `pincode` are removed, the date of birth column is converted to datetime format, and gender values are standardized.

In the Subscription table, subscription start, renewal, and cancellation dates are converted to datetime format. A new `churn_flag` is created using cancellation dates to distinguish churned customers from customers who have not churned.

In the Support table, unnecessary columns are removed, complaint dates are converted to datetime format, and complaint counts are calculated by customer. The latest support record for each customer is retained before the support data is merged with the other tables.

Finally, the three DataFrames are joined using `customerid` to create a combined dataset for further analysis.

## Key Performance Indicators (KPIs)

The notebook calculates or prepares the following business metrics:

- **Customer Churn Rate:** Percentage of customers marked as churned.
- **Customer Retention Rate:** Percentage of customers not marked as churned.
- **Plan-wise Churn Rate:** Churn comparison across Basic, Standard, and Premium plans.
- **State-wise Churn Rate:** Comparison of churn rates across states.
- **Average Revenue per User (ARPU):** Average recorded monthly charges per row in the merged dataset.
- **Average Customer Tenure:** Average duration between subscription start and cancellation dates, or between subscription start and the current date for non-churned customers.
- **Monthly Charges Associated with Churned Customers:** Sum of recorded monthly charges for churned records.
- **Support Escalation Rate:** Percentage of records with an escalation value of `Y`.
- **Complaint Analysis:** Complaint counts derived from support records.

## Exploratory Data Analysis and Visualization

The project uses Matplotlib and Seaborn to explore relationships between churn and customer characteristics. Visualizations include a monthly churn trend, churn rates by subscription plan and state, a correlation heatmap, a pairplot, and comparisons of monthly charges by plan, gender, and churn-risk category.

A churn-risk category is also created from `churn_score` using three groups: Low, Medium, and High. Pivot tables summarize churn rates, monthly charges, and distinct customer counts by subscription plan.

## SQL and Database Integration

SQLite is used to store the Excel workbook's sheets as database tables. SQL queries retrieve table names and load the tables into Pandas DataFrames. This demonstrates the integration of relational database operations with Python-based data analytics.

## Business Objective

The main objective is to understand customer churn behavior, compare subscription plan performance, investigate potential relationships between support escalations and churn, and quantify monthly charges associated with churned customers. These findings can help guide further investigation into customer retention opportunities and customer support improvements.

## Tools and Technologies

- Python
- Pandas and NumPy
- SQL and SQLite
- Matplotlib and Seaborn
- Jupyter Notebook
- Excel data import, data cleaning, joins, feature engineering, aggregation, correlation analysis, and pivot tables

## Limitations and Validation

The customer table contains 500 records, but the number of unique customers and the final merged row count must be verified independently. The support table is reduced to one retained record per customer after calculating complaint counts, so its structure should be considered when interpreting support metrics.

The reported monthly charges associated with churned customers represent a sum of monthly charges, not verified lifetime revenue loss. Correlation indicates association rather than causation. KPI results should be validated after executing the notebook, particularly where missing support values, duplicate records, or categorical encoding may affect the analysis.

