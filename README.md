Sales Management System – Project Introduction

**Introduction**

  The Sales Management System is a relational database project developed using MySQL that helps manage customers, products, orders, and sales transactions efficiently. It is designed to simulate a real-world retail or e-commerce backend system where businesses need to track inventory, customer purchases, and revenue.

In this project, the database named sales_management maintains structured data across multiple related tables such as:

Customers – Stores customer details

Products – Maintains product information and stock

Orders – Records customer purchase orders

Order Details – Stores product-wise order information

The system uses Primary Keys and Foreign Keys to maintain relationships between tables, ensuring data integrity and consistency.

**Purpose of the Project**

    The main objective of this project is to:
    
    Organize sales-related data in a structured format
    
    Maintain relationships between customers and their orders
    
    Track product inventory automatically
    
    Generate meaningful sales reports using SQL queries

Demonstrate advanced database concepts like:

    Joins
    
    Aggregate Functions
    
    Subqueries
    
    Views
    
    Stored Procedures
    
    Triggers

**Real-World Application**

**This system can be used in:**

    Retail Shops
    
    E-commerce Platforms
    
    Wholesale Businesses
    
    Inventory Management Systems
    
    It helps businesses monitor:
    
    Total sales revenue
    
    Category-wise sales
    
    Customer purchase history
    
    Product stock availability

**Technologies Used**

    MySQL – Database Management System
    
    SQL (DDL, DML, DQL) – For creating and managing data

**What is WHERE in SQL?**

    The WHERE clause in SQL is used to filter records from a table based on a specific condition.
    
    It allows you to retrieve only the data that meets certain criteria instead of displaying all records.
**
Create Database**

CREATE DATABASE sales_management;
 USE sales_management;
 
**Customers Table**

              CREATE TABLE customers (
              customer_id INT PRIMARY KEY AUTO_INCREMENT,
              customer_name VARCHAR(100) NOT NULL,
              email VARCHAR(100) UNIQUE,
              city VARCHAR(50)
              );

**Products Table**
        
            CREATE TABLE products (
            product_id INT PRIMARY KEY AUTO_INCREMENT,
            product_name VARCHAR(100) NOT NULL,
            category VARCHAR(50),
            price DECIMAL(10,2) NOT NULL,
            stock INT DEFAULT 0
            );
**
Orders Table**

            CREATE TABLE orders (
            order_id INT PRIMARY KEY AUTO_INCREMENT,
            customer_id INT,
            order_date DATE,
            FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
                ON DELETE CASCADE
                ON UPDATE CASCADE
            );

  **Order Details Table**

          CREATE TABLE order_details (
          order_detail_id INT PRIMARY KEY AUTO_INCREMENT,
          order_id INT,
          product_id INT,
          quantity INT NOT NULL,
          FOREIGN KEY (order_id) REFERENCES orders(order_id)
              ON DELETE CASCADE
              ON UPDATE CASCADE,
          FOREIGN KEY (product_id) REFERENCES products(product_id)
              ON DELETE CASCADE
              ON UPDATE CASCADE
          );
****
What is a Schema in Database**?**

A schema in a database is the structure or blueprint of how the data is organized.

It defines:

Tables

Columns

Data types

Relationships

Constraints (Primary Key, Foreign Key, etc.)

**Types of Schema**
**Database Schema**

Overall design of the database (all tables and relationships).

**Table Schema**

Structure of a single table.

<img width="1536" height="1024" alt="09b8df89-5d3e-4072-924f-3b9a8bae7302" src="https://github.com/user-attachments/assets/34b5f442-11bd-436a-ac33-97a65afb2ec4" />

**What is WHERE Condition in SQL?**

The WHERE condition in SQL is used to filter records from a table based on a specific condition.

SELECT * FROM products
WHERE price > 20000;

<img width="820" height="263" alt="Screenshot 2026-02-24 115746" src="https://github.com/user-attachments/assets/d71ed7f9-2180-4f34-b23b-ca2bf6574673" />


The GROUP BY clause in SQL is used to group rows that have the same values in specified columns and perform aggregate functions on each group.

👉 It is mainly used with:


COUNT()

SUM()

AVG()

MIN()

MAX()

<img width="587" height="310" alt="image" src="https://github.com/user-attachments/assets/ddc58c74-836e-48da-b7ba-b11c9a4ff148" />

what is having and order by?

Both are used with SELECT statements, but they serve different purposes.

HAVING Clause
 What is HAVING?

The HAVING clause is used to filter grouped results after using GROUP BY.

 Important:

WHERE filters rows before grouping

HAVING filters data after grouping

    SELECT customer_id, COUNT(order_id) AS total_orders
    FROM orders
    GROUP BY customer_id
    HAVING COUNT(order_id) > 1; 


<img width="510" height="321" alt="Screenshot 2026-02-24 122021" src="https://github.com/user-attachments/assets/6aef3d9e-6701-4af9-afd6-a62f853037d3" />

    


**what is joins?**

A JOIN in SQL is used to combine rows from two or more tables based on a related column between them.

 It helps you retrieve data stored in different tables as a single result.

** Why JOIN is Needed?**

In relational databases:

Customer details are stored in one table

Order details are stored in another table

To see which customer placed which order, we use JOIN.



    SELECT c.customer_name, COUNT(o.order_id) AS total_orders
    FROM customers c
    LEFT JOIN orders o 
    ON c.customer_id = o.customer_id
    GROUP BY c.customer_name;


<img width="587" height="310" alt="image" src="https://github.com/user-attachments/assets/dc984318-81b5-4540-ace4-d1e4a0a1c4be" />


**what is cte?**

CTE stands for Common Table Expression.

A CTE is a temporary result set that you can define inside a query and use like a table.

 It makes complex queries easier to read and manage.

 Why Use CTE?

Improves readability

Breaks complex queries into steps

Can be reused within the same query

Useful for hierarchical data

    WITH customer_orders AS (
        SELECT customer_id, COUNT(order_id) AS total_orders
        FROM orders
        GROUP BY customer_id
    )
    SELECT *
    FROM customer_orders
    WHERE total_orders > 1;

    






