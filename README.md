# E-Commerce Database Management System
### SQL Server | Database Design | Data Analysis | Business Intelligence

## 1. Project Overview

The **E-Commerce Database Management System** is a relational database project developed using Microsoft SQL Server (MS SQL). It is designed to manage and analyze the core operations of an e-commerce business, including customer information, product inventory, order management, order details, and payment transactions.

The project demonstrates how relational databases can organize business data efficiently while maintaining relationships between multiple entities through Primary Keys and Foreign Keys.

In addition to database development, this project includes a collection of SQL queries designed to extract meaningful business insights, analyze sales performance, monitor product inventory, evaluate customer purchasing behavior, and understand payment trends.

The main objective is to transform raw e-commerce transactional data into structured information that supports business reporting and data-driven decision-making.

## 2. Project Objectives

- Design and implement a relational database using Microsoft SQL Server.
- Organize e-commerce data into structured and related tables.
- Establish relationships using Primary Keys and Foreign Keys.
- Store and manage customer, product, order, and payment information.
- Perform business analysis using SQL aggregate functions.
- Analyze sales performance across different product categories.
- Identify top-selling products and valuable customers.
- Monitor product stock levels and inventory availability.
- Analyze payment methods and payment statuses.
- Generate comprehensive reports using SQL JOIN operations.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Microsoft SQL Server | Relational database management |
| SQL (T-SQL) | Database creation and querying |
| SQL Server Management Studio (SSMS) | Database development and execution |
| Aggregate Functions | Business calculations and analysis |
| JOIN Operations | Combining related database tables |
| GROUP BY | Categorizing and summarizing data |
| CASE Statements | Conditional business analysis |

## 4. Database Architecture

The database is named `EcommerceDBs` and contains five interconnected tables.

### Database Tables

**1. Customers**

Stores customer information and registration details.

| Column | Data Type | Description |
|---|---|---|
| Customer_ID | INT | Unique customer identifier |
| Customer_Name | VARCHAR(100) | Customer's full name |
| Gender | CHAR(1) | Customer gender |
| City | VARCHAR(50) | Customer's city |
| Registration_Date | DATE | Customer registration date |

**2. Products**

Stores product information, categories, prices, and available stock.

| Column | Data Type | Description |
|---|---|---|
| Product_ID | INT | Unique product identifier |
| Product_Name | VARCHAR(100) | Product name |
| Category | VARCHAR(50) | Product category |
| Price | DECIMAL(10,2) | Product price |
| Stock | INT | Available inventory |

**3. Orders**

Stores customer order information and order statuses.

| Column | Data Type | Description |
|---|---|---|
| Order_ID | INT | Unique order identifier |
| Customer_ID | INT | References Customers |
| Order_Date | DATE | Date of order |
| Order_Status | VARCHAR(30) | Current order status |

**4. Order_Details**

Stores individual products associated with each order.

| Column | Data Type | Description |
|---|---|---|
| Detail_ID | INT | Unique detail identifier |
| Order_ID | INT | References Orders |
| Product_ID | INT | References Products |
| Quantity | INT | Quantity purchased |
| Unit_Price | DECIMAL(10,2) | Price per unit |

**5. Payments**

Stores payment transaction information.

| Column | Data Type | Description |
|---|---|---|
| Payment_ID | INT | Unique payment identifier |
| Order_ID | INT | References Orders |
| Payment_Method | VARCHAR(30) | Payment method |
| Payment_Status | VARCHAR(30) | Payment status |
| Amount | DECIMAL(10,2) | Transaction amount |

## 5. Entity Relationship Overview

The database follows a relational structure with the following relationships:

- One customer can place multiple orders.
- One order can contain multiple order details.
- One product can appear in multiple order details.
- One order can have an associated payment record.

### Relationship Structure

```text
Customers
    |
    | 1 : Many
    |
  Orders
    |
    | 1 : Many
    |
Order_Details
    |
    | Many : 1
    |
 Products

Orders
    |
    | 1 : Many (Database Relationship)
    |
 Payments
```

Note: The current database uses a foreign key from Payments to Orders, but does not enforce a unique payment per order.

## 6. Dataset Information

The project includes sample e-commerce transactional data.

| Entity | Total Records |
|---|---:|
| Customers | 8 |
| Products | 8 |
| Orders | 10 |
| Order_Details | 15 |
| Payments | 10 |
| **Total Records** | **51** |

### Sample Business Data

- Customers from Karachi, Lahore, Islamabad, and Multan.
- Products from Electronics, Accessories, and Furniture categories.
- Multiple order statuses, including Delivered, Pending, Cancelled, and Processing.
- Payment methods including Card, Cash, and Online.
- Different payment statuses, including Paid, Unpaid, Pending, and Refunded.

## 7. SQL Analysis and Business Reports

The project contains 16 SQL analysis sections covering different aspects of e-commerce operations.

### 1. Complete Table Overview
Displays all records from the five database tables.

### 2. Customer Overview
Analyzes:
- Total customers.
- Male customers.
- Female customers.

### 3. Product Overview
Analyzes:
- Total products.
- Total available stock.
- Average product price.
- Highest product price.
- Lowest product price.

### 4. Order Overview
Analyzes:
- Total orders.
- Delivered orders.
- Pending orders.
- Cancelled orders.
- Processing orders.

### 5. Sales Overview
Calculates:
- Total sales revenue.
- Average order-line value.
- Highest order-line sale.
- Lowest order-line sale.

### 6. Category-Wise Sales Analysis
Evaluates sales performance across product categories by calculating total quantities sold and revenue generated.

### 7. Top-Selling Products
Identifies the top five products based on total quantity sold and calculates their revenue.

### 8. City-Wise Customer Analysis
Analyzes customer distribution across different cities.

### 9. Payment Method Analysis
Evaluates successful payment transactions by payment method and calculates transaction amounts.

### 10. Payment Status Analysis
Provides an overview of payment transactions grouped by payment status.

### 11. Monthly Sales Analysis
Analyzes delivered sales by year and month to understand monthly revenue trends.

### 12. Customer-Wise Sales Analysis
Identifies customer purchasing behavior by calculating total delivered orders and customer spending.

### 13. Low-Stock Product Analysis
Identifies products with fewer than 20 units available in inventory.

### 14. Order Status Analysis
Provides order counts by status for business reporting and visualization.

### 15. Top Customers Analysis
Identifies the top five customers based on total spending and displays their cities.

### 16. Complete E-Commerce Report
Combines information from all five tables using SQL JOIN operations to generate a comprehensive transactional report.

## 8. SQL Concepts Implemented

This project demonstrates practical implementation of the following SQL concepts:

- CREATE DATABASE
- CREATE TABLE
- Primary Keys
- Foreign Keys
- INSERT INTO
- SELECT
- WHERE
- GROUP BY
- ORDER BY
- INNER JOIN
- LEFT JOIN
- COUNT()
- SUM()
- AVG()
- MAX()
- MIN()
- CASE WHEN
- DISTINCT
- TOP
- YEAR()
- MONTH()
- OBJECT_ID()
- DB_ID()
- Conditional database and table creation

## 9. Database Initialization and Reusability

The database initialization script includes conditional checks to prevent unnecessary database and table creation.

The `DB_ID()` function checks whether the database already exists before creating it.

The `OBJECT_ID()` function checks whether individual tables already exist.

An `IF NOT EXISTS` condition prevents the sample dataset from being inserted again during normal script execution.

This approach allows the database setup script to be executed repeatedly without deleting the existing database or duplicating the original sample records.

## 10. Business Questions Answered

The SQL queries help answer important business questions:

1. How many customers are registered in the business?
2. Which cities have the highest number of customers?
3. How many products are available in the inventory?
4. Which product category generates the highest revenue?
5. Which products are selling the most?
6. What is the total revenue generated from delivered orders?
7. How many orders are delivered, pending, cancelled, or processing?
8. Which payment method is used most frequently?
9. How much revenue is generated each month?
10. Which customers contribute the most to business revenue?
11. Which products have low inventory levels?
12. What is the overall payment status distribution?

## 11. Potential Business Intelligence Applications

The structured database and analysis queries can serve as a foundation for business intelligence and reporting solutions.

Potential dashboard visualizations include:

- Total Customers KPI.
- Total Products KPI.
- Total Orders KPI.
- Total Delivered Sales KPI.
- Monthly Sales Trend.
- Category-Wise Revenue Chart.
- Top-Selling Products Chart.
- Customer Distribution by City.
- Order Status Distribution.
- Payment Method Analysis.
- Top Customers Report.
- Low-Stock Products Table.

The database can also be connected to Microsoft Power BI to develop an interactive E-Commerce Sales and Performance Dashboard.

## 12. How to Run the Project

**Requirements:**
- Microsoft SQL Server.
- SQL Server Management Studio (SSMS).

**Execution Steps:**

1. Install and open SQL Server Management Studio.
2. Connect to your SQL Server instance.
3. Open a new query window.
4. Copy the SQL script into the query editor.
5. Execute the script.
6. The database `EcommerceDBs` will be created if it does not already exist.
7. The five tables and sample records will be initialized if they are not already present.
8. Execute the analysis queries to explore business insights.

## 13. Project Limitations and Future Improvements

This project is a foundational SQL database and business analysis implementation. Future improvements could include:

- Adding stored procedures for reusable business reports.
- Implementing SQL views for frequently used analysis.
- Creating indexes to improve query performance.
- Adding constraints for data validation.
- Implementing triggers for automated inventory updates.
- Introducing customer and product performance metrics.
- Developing a Power BI dashboard.
- Expanding the dataset with more realistic transactional records.
- Adding discount, shipping, returns, and tax information.
- Improving payment-to-order validation and transaction handling.

## 14. Learning Outcomes

Through this project, practical experience was gained in:

- Relational database design.
- Database creation and management.
- Defining table relationships.
- Managing structured business data.
- Writing analytical SQL queries.
- Performing multi-table JOIN operations.
- Using aggregate functions for business reporting.
- Analyzing customer and product performance.
- Generating business-focused reports.

## 15. Conclusion

The E-Commerce Database Management System demonstrates how Microsoft SQL Server can be used to design, manage, and analyze structured business data.

By combining relational database design with practical SQL queries, the project provides insights into customer behavior, product performance, sales trends, order management, inventory levels, and payment transactions.

It establishes a foundation for more advanced database development and business intelligence solutions, including interactive reporting through Microsoft Power BI.

---

**Project Name:** E-Commerce Database Management System  
**Database:** EcommerceDBs  
**Database Platform:** Microsoft SQL Server  
**Query Language:** T-SQL  
**Project Type:** SQL Database Development & Business Data Analysis  
**Status:** Completed (Foundational Version)

