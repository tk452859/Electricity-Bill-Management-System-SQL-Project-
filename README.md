# Electricity Bill Management System

A robust and efficient **SQL Database Project** designed to automate the core operations of an electricity utility provider. This system manages customer information, meter data, electricity consumption tracking, bill generation, and payment processing.

## Features

-   **Customer Management**: Store and manage customer details.
-   **Meter Management**: Link multiple meters to customers.
-   **Automated Billing**: Calculate bills based on meter readings and tariffs.
-   **Payment Processing**: Record payments and update bill statuses.
-   **Data Integrity**: Enforced through primary and foreign keys.

## Database Schema

The main tables include:
-   `customers`: Stores customer details.
-   `meters`: Links meters to customers.
-   `bills`: Stores billing records and calculates charges.
-   `payments`: Tracks payment transactions.


## Technology Stack

-   **Database**: MySQL

## Installation & Setup

1.  **Prerequisites**: Ensure MySQL is installed and running.
2.  **Create the Database**:
    ```sql
    CREATE DATABASE electricity_bill_db;
    USE electricity_bill_db;
    ```
3.  **Import the Schema**:
    -   Execute the `electricity_bill_system.sql` script in your MySQL client to create the tables and sample data.

## Example Queries

**1. Get all bills for a customer:**
```sql
SELECT c.name, b.bill_id, b.amount, b.status
FROM customers c
JOIN meters m ON c.customer_id = m.customer_id
JOIN bills b ON m.meter_id = b.meter_id
WHERE c.customer_id = 1;
