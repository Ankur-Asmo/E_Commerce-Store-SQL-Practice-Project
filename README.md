# E_Commerce-SQL-Practice-Project

## Overview
This repository contains a **SQL practice project** based on an **E-Commerce Store database**.  
It is designed to demonstrate practical SQL skills for data analytics, reporting, and business intelligence use cases.  

The project simulates a real-world e-commerce environment with tables for products and orders. 
It showcases how SQL can be used to answer business questions, generate insights, and prepare datasets for dashboards.

---

## Project Structure
**Database Script**  
  SQL file to create and populate the e-commerce database with sample data.
**Practice Queries**  
  A collection of SQL queries covering:
  - Joins (INNER, LEFT, RIGHT, FULL OUTER, CROSS JOIN)
  - Aggregations (SUM, COUNT, AVG, MIN, MAX)
  - Filtering and Sorting
**Business Scenarios**  
  Queries designed to solve real-world problems such as:
  - Top-selling products
  - total revenue earned per product
  - products even if they were never ordered
## SQL Queries For Diffrent Insights

**Q1.Show each order along with the product name and price.**
```sql
SELECT o.order_id, o.customer_name, p.product_name, p.price
FROM orders o
JOIN products p ON o.product_id = p.product_id;
```

**Q2.Show all products even if they were never ordered.**
```sql
SELECT p.product_name, o.order_id
FROM products p
LEFT JOIN orders o ON p.product_id = o.product_id;
```

**Q3.Show orders for only 'Electronics' category.**
```sql
SELECT o.order_id, p.product_name, p.category
FROM orders o
JOIN products p ON o.product_id = p.product_id
WHERE p.category = 'Electronics';
```

**Q4.List all orders sorted by product price (high to low).**
```sql
SELECT o.order_id, p.product_name, p.price
FROM orders o
JOIN products p ON o.product_id = p.product_id
ORDER BY p.price DESC;
```
**Q5.Show number of orders placed for each product.**
```sql
SELECT p.product_name, COUNT(o.order_id) AS total_orders
FROM products p
LEFT JOIN orders o ON p.product_id = o.product_id
GROUP BY p.product_name;
```

**Q6.Show total revenue earned per product.**
```sql
SELECT p.product_name, SUM(o.quantity * p.price) AS revenue
FROM products p
JOIN orders o ON p.product_id = o.product_id
GROUP BY p.product_name;
```

**Q7.Show products where total order revenue > ₹2000.**
```sql
SELECT p.product_name, SUM(o.quantity * p.price) AS total_revenue
FROM products p
JOIN orders o ON p.product_id = o.product_id
GROUP BY p.product_name
HAVING SUM(o.quantity * p.price) > 2000;
```

**Q8.Show unique customers who ordered 'Fitness' products.**
```sql
SELECT DISTINCT o.customer_name
FROM orders o
JOIN products p ON o.product_id = p.product_id
WHERE p.category = 'Fitness';
```
## Learning Objectives
- Strengthen SQL fundamentals through hands-on practice.
- Apply SQL to **business analytics scenarios**.
- Build a portfolio-ready project showcasing:
  - Query optimization
  - Data modeling
  - Analytical problem-solving
