# 🛍️ Retail Sales Data Analysis Project

## 📖 Overview
This project analyzes retail sales data using **SQL Server** to uncover patterns in sales performance, customer behavior, and product trends. The goal is to provide actionable insights that can help improve sales strategy, marketing, and customer retention.

---
## 🧱 Database Setup
**Table Name:** `['SQL - Retail Sales Analysis_utf$']`

**Columns:**
- transactions_id
- sale_date
- sale_time
- customer_id
- gender
- age
- category
- quantity
- price_per_unit
- cogs
- total_sale

---

## 🧹 Data Cleaning
The cleaning process involved removing rows with missing or null values across all key columns.

```sql
DELETE FROM ['SQL - Retail Sales Analysis_utf$'] 
WHERE 
transactions_id IS NULL
OR sale_date IS NULL
OR sale_time IS NULL
OR customer_id IS NULL
OR gender IS NULL
OR age IS NULL
OR category IS NULL
OR quantity IS NULL
OR price_per_unit IS NULL
OR cogs IS NULL
OR total_sale IS NULL;
```

---

## 🔍 Data Exploration
### Total Sales
```sql
SELECT COUNT(*) as total_sales FROM ['SQL - Retail Sales Analysis_utf$'];
```

### Unique Customers
```sql
SELECT COUNT(DISTINCT customer_id) as total_customers FROM ['SQL - Retail Sales Analysis_utf$'];
```

### Unique Categories
```sql
SELECT DISTINCT category FROM ['SQL - Retail Sales Analysis_utf$'];
```

---

## 📊 Key Business Questions & SQL Solutions

### Q1: Retrieve all columns for sales made on '2022-11-05'
```sql
SELECT * FROM ['SQL - Retail Sales Analysis_utf$']
WHERE sale_date = '2022-11-05';
```

### Q2: Transactions where category = 'Clothing' and quantity sold > 4
```sql
SELECT * FROM ['SQL - Retail Sales Analysis_utf$']
WHERE category = 'Clothing' AND quantity >= 4;
```

### Q3: Calculate total sales (total_sale) for each category
```sql
SELECT category, SUM(total_sale) AS net_sale, COUNT(*) AS total_orders
FROM ['SQL - Retail Sales Analysis_utf$']
GROUP BY category;
```

### Q4: Average age of customers in 'Beauty' category
```sql
SELECT ROUND(AVG(age), 3) AS Avg_age
FROM ['SQL - Retail Sales Analysis_utf$']
WHERE category = 'Beauty';
```

### Q5: Transactions where total_sale > 1000
```sql
SELECT * FROM ['SQL - Retail Sales Analysis_utf$']
WHERE total_sale > 1000;
```

### Q6: Number of transactions by gender and category
```sql
SELECT category, gender, COUNT(*) AS total_trans
FROM ['SQL - Retail Sales Analysis_utf$']
GROUP BY category, gender;
```

### Q7: Average monthly sales and best-selling months
```sql
SELECT YEAR(sale_date) AS year, MONTH(sale_date) AS month, AVG(total_sale) AS avg_total_sale
FROM ['SQL - Retail Sales Analysis_utf$']
GROUP BY YEAR(sale_date), MONTH(sale_date)
ORDER BY YEAR(sale_date), avg_total_sale DESC;
```

### Q8: Top 5 customers by total sales
```sql
SELECT TOP 5 customer_id, SUM(total_sale) AS total_sale
FROM ['SQL - Retail Sales Analysis_utf$']
GROUP BY customer_id
ORDER BY total_sale DESC;
```

### Q9: Unique customers by category
```sql
SELECT COUNT(DISTINCT customer_id) AS unique_customers, category
FROM ['SQL - Retail Sales Analysis_utf$']
GROUP BY category;

```
### Q10: create each shift and number of orders (Example Morning <=12, Afternoon Between 12 & 17, Evening >17)

WITH hourly_sale
AS
(
SELECT *,
    CASE
        WHEN EXTRACT(HOUR FROM sale_time) < 12 THEN 'Morning'
        WHEN EXTRACT(HOUR FROM sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
        ELSE 'Evening'
    END as shift
FROM retail_sales
)
SELECT 
    shift,
    COUNT(*) as total_orders    
FROM hourly_sale
GROUP BY shift

```

## 📊 Findings

1. **Sales Volume** — The dataset contains a large number of transactions across multiple product categories.
2. **Customer Insights** — A broad customer base with some categories having more repeat customers.
3. **Category Performance** — Clothing, Electronics, and Beauty generated the highest sales.
4. **High-Value Transactions** — Some transactions exceeded ₦1000, indicating premium purchases.
5. **Gender-Based Analysis** — Female customers dominate Beauty and Clothing; males dominate Electronics.
6. **Age Demographics** — Younger customers drive Beauty category sales.
7. **Seasonal and Monthly Trends** — Sales peaks during November and December.
8. **Top Customers** — Top 5 customers account for a large share of total revenue.
9. **Unique Customer Engagement** — Each category attracts distinct customer segments.
10. **Shift-Based Transactions** — Afternoon shift records the highest sales volume.

---

## 🧾 Conclusion

The project provides insights into customer behavior, category performance, and sales trends. SQL-based data analysis revealed opportunities for improving marketing strategies, resource allocation, and operational performance. It demonstrates how data-driven decision-making can enhance overall business productivity.

---

## 💡 Recommendations

1. Focus on high-performing categories (Clothing, Beauty).
2. Develop customer loyalty and retention programs.
3. Implement targeted marketing based on gender and age insights.
4. Use seasonal promotions during peak months.
5. Optimize staffing and inventory for afternoon shifts.
6. Offer cross-category bundles to boost average sales.
7. Continuously monitor data for ongoing business intelligence.

---

## 🛠️ Tools Used
- Microsoft SQL Server
- SQL Queries for Data Analysis
- Excel for initial data preparation

---

## 👤 Author
**Ajayi dayo**  
Data Analyst 
