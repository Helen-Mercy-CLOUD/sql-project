# sql-project


 Project Title: Sales Management System (MySQL)

** Project Description**

This project manages:

* Customers
* Products
* Orders
* Order Details

**It demonstrates:**

* Joins
* Group By
* Aggregate Functions
* Subqueries
* Views
* Stored Procedures
* Triggers

 **Create Database**


CREATE DATABASE sales_management;
USE sales_management;


** Create Tables**

**1. Customers Table**

CREATE TABLE customers (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(100),
    email VARCHAR(100),
    city VARCHAR(50)
);


** 2. Products Table**


CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(100),
    category VARCHAR(50),
    price DECIMAL(10,2),
    stock INT
);



 **3. Orders Table**


CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

**4. Order Details Table**


CREATE TABLE order_details (
    order_detail_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    product_id INT,
    quantity INT,
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);

** Insert Sample Data**


INSERT INTO customers (customer_name, email, city) VALUES
('Helen Mercy', 'helen@gmail.com', 'Chennai'),
('Arun Kumar', 'arun@gmail.com', 'Bangalore'),
('Priya Sharma', 'priya@gmail.com', 'Mumbai');

INSERT INTO products (product_name, category, price, stock) VALUES
('Laptop', 'Electronics', 60000, 10),
('Mobile', 'Electronics', 25000, 20),
('Office Chair', 'Furniture', 8000, 15),
('Desk', 'Furniture', 12000, 8);

INSERT INTO orders (customer_id, order_date) VALUES
(1, '2025-01-10'),
(2, '2025-01-15'),
(1, '2025-02-01');

INSERT INTO order_details (order_id, product_id, quantity) VALUES
(1, 1, 1),
(1, 3, 2),
(2, 2, 1),
(3, 4, 1);

 **Important SQL Queries (Interview Ready)
**


 Basic Queries

1. View All Customers


SELECT * FROM customers;


 2. View All Products


SELECT * FROM products;
Perfect Helen 👍
Here is a **complete SQL Project with Tables + Sample Data + 25 Important Queries** that you can upload to GitHub or explain in interviews.

---

# 📊 Project Title: Sales Management System (MySQL)

## 🔹 Project Description

This project manages:

* Customers
* Products
* Orders
* Order Details

It demonstrates:

* Joins
* Group By
* Aggregate Functions
* Subqueries
* Views
* Stored Procedures
* Triggers

---

# 🔹 1️⃣ Create Database

```sql
CREATE DATABASE sales_management;
USE sales_management;
```

---

# 🔹 2️⃣ Create Tables

## 1. Customers Table

```sql
CREATE TABLE customers (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(100),
    email VARCHAR(100),
    city VARCHAR(50)
);
```

---

## 2. Products Table

```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(100),
    category VARCHAR(50),
    price DECIMAL(10,2),
    stock INT
);
```

---

## 3. Orders Table

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

---

## 4. Order Details Table

```sql
CREATE TABLE order_details (
    order_detail_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    product_id INT,
    quantity INT,
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);
```

---

# 🔹 3️⃣ Insert Sample Data

```sql
INSERT INTO customers (customer_name, email, city) VALUES
('Helen Mercy', 'helen@gmail.com', 'Chennai'),
('Arun Kumar', 'arun@gmail.com', 'Bangalore'),
('Priya Sharma', 'priya@gmail.com', 'Mumbai');

INSERT INTO products (product_name, category, price, stock) VALUES
('Laptop', 'Electronics', 60000, 10),
('Mobile', 'Electronics', 25000, 20),
('Office Chair', 'Furniture', 8000, 15),
('Desk', 'Furniture', 12000, 8);

INSERT INTO orders (customer_id, order_date) VALUES
(1, '2025-01-10'),
(2, '2025-01-15'),
(1, '2025-02-01');

INSERT INTO order_details (order_id, product_id, quantity) VALUES
(1, 1, 1),
(1, 3, 2),
(2, 2, 1),
(3, 4, 1);
```

---

# 🔥 4️⃣ Important SQL Queries (Interview Ready)

---

## 🔹 Basic Queries

### 1. View All Customers

```sql
SELECT * FROM customers;
```

### 2. View All Products

```sql
SELECT * FROM products;
```

### 3. Products Above 20,000

```sql
SELECT * FROM products
WHERE price > 20000;
```

---

## 🔹 Join Queries

### 4. Orders with Customer Name

```sql
SELECT o.order_id, c.customer_name, o.order_date
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;
```

### 5. Order Details with Product Name

```sql
SELECT od.order_id, p.product_name, od.quantity
FROM order_details od
JOIN products p ON od.product_id = p.product_id;
```

---

## 🔹 Aggregate Queries

### 6. Total Orders Per Customer

```sql
SELECT c.customer_name, COUNT(o.order_id) AS total_orders
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
```

### 7. Total Sales Amount

```sql
SELECT SUM(p.price * od.quantity) AS total_sales
FROM order_details od
JOIN products p ON od.product_id = p.product_id;
```

### 8. Highest Priced Product

```sql
SELECT * FROM products
ORDER BY price DESC
LIMIT 1;
```

---

## 🔹 Group By Queries

### 9. Sales by Category

```sql
SELECT p.category,
       SUM(p.price * od.quantity) AS category_sales
FROM order_details od
JOIN products p ON od.product_id = p.product_id
GROUP BY p.category;
```

---

## 🔹 Subqueries

### 10. Customers Who Placed Orders

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders);
```

### 11. Products Never Ordered

```sql
SELECT product_name
FROM products
WHERE product_id NOT IN (SELECT product_id FROM order_details);
```

---

## 🔹 Date Queries

### 12. Orders in January 2025

```sql
SELECT * FROM orders
WHERE MONTH(order_date) = 1 AND YEAR(order_date) = 2025;
```

---

## 🔹 Update & Delete

### 13. Update Stock

```sql
UPDATE products
SET stock = stock - 1
WHERE product_id = 1;
```

### 14. Delete Customer

```sql
DELETE FROM customers
WHERE customer_id = 3;
```

---

# 🔥 5️⃣ Advanced Features

---

## 🔹 View

```sql
CREATE VIEW sales_summary AS
SELECT c.customer_name,
       SUM(p.price * od.quantity) AS total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
JOIN order_details od ON o.order_id = od.order_id
JOIN products p ON od.product_id = p.product_id
GROUP BY c.customer_name;
```

---

## 🔹 Stored Procedure

```sql
DELIMITER //

CREATE PROCEDURE GetCustomerOrders(IN cust_id INT)
BEGIN
    SELECT o.order_id, o.order_date
    FROM orders o
    WHERE o.customer_id = cust_id;
END //

DELIMITER ;
```

Call:

```sql
CALL GetCustomerOrders(1);
```

---

 Trigger (Auto Reduce Stock)


DELIMITER //

CREATE TRIGGER reduce_stock
AFTER INSERT ON order_details
FOR EACH ROW
BEGIN
    UPDATE products
    SET stock = stock - NEW.quantity
    WHERE product_id = NEW.product_id;
END //

DELIMITER ;




### 3. Products Above 20,000

```sql
SELECT * FROM products
WHERE price > 20000;
```

---

## 🔹 Join Queries

### 4. Orders with Customer Name

```sql
SELECT o.order_id, c.customer_name, o.order_date
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;
```

### 5. Order Details with Product Name

```sql
SELECT od.order_id, p.product_name, od.quantity
FROM order_details od
JOIN products p ON od.product_id = p.product_id;
```

---

## 🔹 Aggregate Queries

### 6. Total Orders Per Customer

```sql
SELECT c.customer_name, COUNT(o.order_id) AS total_orders
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
```

### 7. Total Sales Amount

```sql
SELECT SUM(p.price * od.quantity) AS total_sales
FROM order_details od
JOIN products p ON od.product_id = p.product_id;
```

### 8. Highest Priced Product

```sql
SELECT * FROM products
ORDER BY price DESC
LIMIT 1;
```

---

## 🔹 Group By Queries

### 9. Sales by Category

```sql
SELECT p.category,
       SUM(p.price * od.quantity) AS category_sales
FROM order_details od
JOIN products p ON od.product_id = p.product_id
GROUP BY p.category;
```

---

## 🔹 Subqueries

### 10. Customers Who Placed Orders

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders);
```

### 11. Products Never Ordered

```sql
SELECT product_name
FROM products
WHERE product_id NOT IN (SELECT product_id FROM order_details);
```

---

## 🔹 Date Queries

### 12. Orders in January 2025

```sql
SELECT * FROM orders
WHERE MONTH(order_date) = 1 AND YEAR(order_date) = 2025;
```

---

## 🔹 Update & Delete

### 13. Update Stock

```sql
UPDATE products
SET stock = stock - 1
WHERE product_id = 1;
```

### 14. Delete Customer

```sql
DELETE FROM customers
WHERE customer_id = 3;
```

---

# 🔥 5️⃣ Advanced Features

---

## 🔹 View

```sql
CREATE VIEW sales_summary AS
SELECT c.customer_name,
       SUM(p.price * od.quantity) AS total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
JOIN order_details od ON o.order_id = od.order_id
JOIN products p ON od.product_id = p.product_id
GROUP BY c.customer_name;
```

---

** Stored Procedure
**

DELIMITER //

CREATE PROCEDURE GetCustomerOrders(IN cust_id INT)
BEGIN
    SELECT o.order_id, o.order_date
    FROM orders o
    WHERE o.customer_id = cust_id;
END //

DELIMITER ;


Call:


CALL GetCustomerOrders(1);


** Trigger (Auto Reduce Stock)
**

DELIMITER //

CREATE TRIGGER reduce_stock
AFTER INSERT ON order_details
FOR EACH ROW
BEGIN
    UPDATE products
    SET stock = stock - NEW.quantity
    WHERE product_id = NEW.product_id;
END //

DELIMITER ;






