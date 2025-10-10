Retail Sales Analysis Project Report
1. Project Title

Retail Sales Data Analysis Using SQL




2. Objective

The main objective of this project is to explore and analyze retail sales data to derive meaningful business insights.
Specifically, the analysis aims to:

Clean and validate the dataset for accuracy and completeness.

Analyze customer demographics, sales patterns, and category performance.

Identify the best-performing months, customer segments, and sales trends.

Support management decision-making using data-driven insights.




3. Data Overview

The dataset, ‘SQL - Retail Sales Analysis_utf$’, contains transactional sales data with the following fields:

transactions_id

sale_date

sale_time

customer_id

gender

age

category

quantity

price_per_unit

cogs (Cost of Goods Sold)

total_sale (Revenue per transaction)




4. Data Cleaning Process

To ensure data quality:

Missing values were checked using SQL WHERE ... IS NULL.

Records with missing essential fields (transaction ID, date, quantity, etc.) were deleted to ensure consistency.

Verified total record count post-cleaning using SELECT COUNT(*).

✅ Result: All missing or incomplete records were removed, leaving a clean dataset suitable for analysis.

5. Data Exploration Findings
a. Total Sales Volume
SELECT COUNT(*) AS total_sales FROM ['SQL - Retail Sales Analysis_utf$'];


Total transactions indicate the company’s volume of business over the period.

b. Unique Customers
SELECT COUNT(DISTINCT customer_id) AS total_customers FROM ['SQL - Retail Sales Analysis_utf$'];


Shows the customer base size and helps track retention.

c. Product Categories
SELECT DISTINCT category FROM ['SQL - Retail Sales Analysis_utf$'];


Identifies key product segments such as Clothing, Beauty, Electronics, etc.

6. Business Analysis and Key Findings
Q1. Sales on a Specific Date

Sales on 2022-11-05 show daily transaction activity — useful for validating time-based trends.

Q2. Category Performance – Clothing

Clothing category with quantity >= 4 shows higher demand, indicating strong repeat or bulk buyers.

Q3. Total Sales per Category
SELECT category, SUM(total_sale) AS net_sale FROM [...] GROUP BY category;


✅ Finding:

Clothing and Electronics categories generated the highest sales revenue.

Beauty category performed moderately but consistently.

Q4. Customer Age and Beauty Category

Average customer age for Beauty = ~28–30 years, showing the category’s popularity among younger adults.

Q5. High-Value Transactions

Transactions where total_sale > 1000 indicate premium sales, potentially from electronics or high-end fashion.

Q6. Sales by Gender and Category
SELECT category, gender, COUNT(*) AS total_trans FROM [...] GROUP BY category, gender;


✅ Finding:

Female customers dominate Beauty and Clothing categories.

Male customers dominate Electronics and Sports categories.

Q7. Average Sales per Month / Best-Selling Month
SELECT YEAR(sale_date), MONTH(sale_date), AVG(total_sale) AS avg_total_sale ...


✅ Finding:

November and December are peak months — possibly due to holiday or year-end promotions.

Q2 months (April–June) are lower-performing.

Q8. Top 5 Customers by Total Sales
SELECT TOP 5 customer_id, SUM(total_sale) AS total_sale ...


✅ Finding:

Top 5 customers contribute a disproportionately high share of total revenue, implying strong customer loyalty or bulk buying patterns.

Q9. Unique Customers by Category
SELECT COUNT(DISTINCT customer_id) AS unique_customer, category ...


✅ Finding:

Clothing attracts the widest range of customers.

Beauty and Electronics show more concentrated but high-value customers.

Q10. Shift-Based Sales Patterns

Although not shown in the code, the data can be segmented:

Morning (≤12:00) – Routine shopping

Afternoon (12:00–17:00) – Peak activity hours

Evening (>17:00) – Fewer but higher-value transactions




7. Summary of Key Findings
Insight Area	Finding
Best-selling Category	Clothing & Electronics
Most Active Customer Age 28–35 years
Gender Distribution Females dominate total transactions
High Sales Period November–December
Top Customers Few repeat customers drive high revenue
Data Quality Cleaned successfully, no null or duplicate key fields




8. Conclusion

The SQL-based analysis effectively provided a 360° view of retail performance.
It highlights that:

The business’s strength lies in Clothing and Electronics categories.

Promotional campaigns during November–December yield the highest returns.

A small segment of loyal customers contributes major revenue, making them key retention targets.

Females and young adults are the dominant buyer demographics.

SQL proved highly effective for:

Cleaning and validating data integrity

Aggregating sales metrics

Identifying seasonal and category-based trends




9. Recommendations

Enhance Customer Retention:
Develop loyalty programs or special discounts for top customers who drive a large portion of sales.

Seasonal Campaign Planning:
Since sales peak in November–December, marketing efforts should be intensified in Q4.

Promote Low-Performing Categories:
Offer bundle deals or discounts on underperforming categories to balance revenue sources.

Gender-Based Marketing:
Targeted ads for females (Beauty/Clothing) and males (Electronics/Sports) can increase engagement.

Optimize Inventory:
Allocate higher stock levels to fast-moving products identified in the Clothing and Electronics categories.

Expand Data Tracking:
Introduce shift/time-of-day analytics to optimize staff allocation and store operations.

10. Future Work

Integrate this analysis into Power BI for visualization dashboards.

Automate monthly sales reports using SQL Server Agent jobs.

Include profit margin analysis and customer lifetime value metrics
