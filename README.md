**Electricity Bill Management System**
Project Overview
This project is a relational database system designed to manage electricity billing data efficiently. It simulates a real-world electricity provider’s database with customers, accounts, billing records, tariffs, and invoices.

**Database Structure & Tables**
Table Name	Description
**customer:	Stores customer details including name, address, city, and state.
accounts:	Stores account details linked to customers.
billing	Records: monthly electricity usage, units consumed, rate per unit, and total bill amount.
elec_board:	Represents various electricity boards/companies supplying power.
tariff:	Defines different tariff types for billing calculation.
invoice:	Stores invoice details linking meter readings, tariffs, and electricity boards.
admin:	Contains admin users managing customer data.**

**Relationships
Each account belongs to a customer (accounts.cust_id → customer.cust_id).
Each billing record links to an account and customer (billing.acc_id, billing.cust_id).
Invoices relate to electricity boards, tariffs, and billing via foreign keys.
Admins are linked to customers for administrative purposes.**

Sample Queries
/*Basic Data Retrieval*/

SELECT * FROM customer;
SELECT * FROM billing WHERE cust_id = 111;

/*Filtering and Sorting*/
-- Bills greater than ₹5000
SELECT * FROM billing WHERE total_amount > 5000;

-- Sort bills by amount descending
SELECT * FROM billing ORDER BY total_amount DESC;

/*Aggregations and Grouping*/

-- Total revenue collected
SELECT SUM(total_amount) AS Total_Revenue FROM billing;

-- Average monthly units per customer
SELECT cust_id, AVG(monthly_units) AS Avg_Units FROM billing GROUP BY cust_id;

-- Top 5 customers by revenue
SELECT cust_id, SUM(total_amount) AS TotalPaid
FROM billing
GROUP BY cust_id
ORDER BY TotalPaid DESC
LIMIT 5;

/*Views*/

CREATE VIEW high_value_customers AS
SELECT cust_id, SUM(total_amount) AS total_paid
FROM billing
GROUP BY cust_id
HAVING total_paid > 5000;

/*Join Example*/

SELECT c.cust_name, b.monthly_units, b.total_amount
FROM customer c
JOIN billing b ON c.cust_id = b.cust_id;



**How to Run
Import the SQL dump file into your MySQL server or use MySQL Workbench.
The database smart_meter along with all tables and sample data will be created automatically.
Run example queries or modify for your use case.**

**Technologies Used
MySQL
SQL Queries, Joins, Views, Constraints
Relational Database Design**

**Future Enhancements
Add stored procedures for automated bill calculation.
Implement triggers to update invoice records automatically.

Develop a front-end interface to visualize reports and billing info.**

