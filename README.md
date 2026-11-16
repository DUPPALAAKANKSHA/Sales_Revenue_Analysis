# Sales_Revenue_Analysis
                           Sales and Revenue Analysis
                              Project Description
                              
The Sales and Revenue Analysis project is a relational database management system
developed using MySQL to manage and analyse sales-related information.
The project maintains details of customers, product categories, products, customer orders,
order items and payments. It helps businesses analyse sales performance, track revenue,
monitor product demand, understand customer purchasing behaviour and generate
meaningful business reports.
This project demonstrates practical SQL skills through database design, data manipulation,
data retrieval, joins, subqueries, aggregate functions, views and indexes.

                                   Features
                                   
• Customer Management: Store customer information, contact details and registration
dates.
• Category Management: Organize products into different categories.
• Product Management: Maintain product prices, stock quantities and availability.
• Order Management: Track customer orders and their statuses.
• Order Item Management: Maintain products, quantities and selling prices for each
order.
• Payment Management: Track payment amounts, methods and payment statuses.
• Revenue Analysis: Calculate total, monthly, product-wise and category-wise revenue.
• Customer Analysis: Identify frequent customers and customer-wise purchases.
• SQL Views: Create reusable views for business reporting.
• Indexing: Improve query performance for frequently searched columns.

                           Technologies Used
                           
• MySQL 8+ - Relational database management
• SQL - Database creation and querying
• MySQL Workbench - SQL development and execution
• ER Diagram - Database relationship modelling

                           Database Structure
                           
Database Name: 'sales_analysis'
The database consists of six interconnected tables.
• customers - Stores customer information
• categories - Stores product category details
• products - Stores product information and stock
• orders - Stores customer order information
• order_items - Stores products and quantities associated with orders
• payments - Stores payment transaction details

Entity Relationships
• One customer can place multiple orders.
• One category can contain multiple products.
• One order can contain multiple order items.
• One product can appear in multiple order items.
• One order can have multiple payment records.

                           Installation Steps
                           
Step 1: Install MySQL
Download and install MySQL Server and MySQL Workbench.
Step 2: Clone the repository
Step 3: Navigate to the project folder
Step 4: Open MySQL Workbench
Connect to your MySQL server.
Step 5: Create the database
 ```sql
CREATE DATABASE sales_analysis;
USE sales_analysis;
 ```
                      How to Execute SQL Files
                      
Execute the SQL scripts in the following order:
• create_database.sql - Create database
• create_tables.sql - Create all six tables
• insert_data.sql - Insert sample records
• queries.sql - Joins and subqueries
• functions.sql - Aggregate,Numeric, String, Date,and NULL-handling Functions
and grouping queries
• views.sql - Create reporting views
Open each file in MySQL Workbench and execute it using the lightning icon.

                    Sample SQL Queries
                    
Display all customers
SELECT * FROM customers;
Find the top five expensive products
SELECT product_name, price
FROM products
ORDER BY price DESC
LIMIT 5;

Display customer names and their order details
SELECT
 c.customer_name,
 o.order_id,
 o.order_date,
 o.order_status
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;

Calculate total delivered revenue
SELECT
 SUM(oi.quantity * oi.unit_price) AS total_revenue
FROM orders o
INNER JOIN order_items oi
ON o.order_id = oi.order_id
WHERE o.order_status = 'Delivered';

Find category-wise revenue
SELECT
 c.category_name,
 SUM(oi.quantity * oi.unit_price) AS total_revenue
FROM categories c
INNER JOIN products p
ON c.category_id = p.category_id
INNER JOIN order_items oi
ON p.product_id = oi.product_id
INNER JOIN orders o
ON oi.order_id = o.order_id
WHERE o.order_status = 'Delivered'
GROUP BY c.category_id, c.category_name;

Find customers who have never placed an order
SELECT
 c.customer_id,
 c.customer_name
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;

Generate a monthly revenue report
SELECT
 YEAR(o.order_date) AS sales_year,
 MONTH(o.order_date) AS sales_month,
 SUM(oi.quantity * oi.unit_price) AS monthly_revenue
FROM orders o
INNER JOIN order_items oi
ON o.order_id = oi.order_id
WHERE o.order_status = 'Delivered'
GROUP BY YEAR(o.order_date), MONTH(o.order_date)
ORDER BY sales_year, sales_month;

                    Future Enhancements
                    
• Develop a web-based sales management application.
• Integrate Python for automated data analysis.
• Build interactive dashboards using Power BI or Tableau.
• Implement inventory alerts for low-stock products.
• Add sales forecasting using Machine Learning.
• Generate automated monthly sales reports.
• Integrate customer segmentation and purchasing behaviour analysis.
