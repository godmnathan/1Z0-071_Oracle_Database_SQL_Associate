# TechCorp Database Schema

## Entity-Relationship Diagram

```
                                   +----------------+
                                   |    REGIONS     |
                                   +----------------+
                                   | region_id (PK) |
                                   | region_name    |
                                   +----------------+
                                          |
                                          | 1
                                          |
                                          v
                                   +----------------+
                                   |   COUNTRIES    |
                                   +----------------+
                                   | country_id (PK)|
                                   | country_name   |
                                   | region_id (FK) |
                                   +----------------+
                                          |
                                          | 1
                                          |
                                          v
                      +-------------------+-------------------+
                      |                                       |
                      v                                       v
          +----------------+                        +----------------+
          |   LOCATIONS    |                        |  CURRENCIES    |
          +----------------+                        +----------------+
          | location_id (PK)|                       | currency_id (PK)|
          | street_address  |                       | currency_name   |
          | postal_code     |                       | country_id (FK) |
          | city            |                       +----------------+
          | state_province  |
          | country_id (FK) |
          +----------------+
                  |
                  | 1
                  |
                  v
          +----------------+
          |  DEPARTMENTS   |
          +----------------+
          | department_id  |
          | department_name|
          | manager_id (FK)|<----+
          | location_id (FK)|    |
          +----------------+     |
                  |              |
                  | 1            |
                  |              |
                  v              |
          +----------------+     |
          |   EMPLOYEES    |     |
          +----------------+     |
          | employee_id (PK)|    |
          | first_name      |    |
          | last_name       |    |
          | email           |    |
          | phone_number    |    |
          | hire_date       |    |
          | job_id (FK)     |----+
          | salary          |    |
          | commission_pct  |    |
          | manager_id (FK) |----+
          | department_id   |
          +----------------+
                  |
                  | 1
                  |
                  v
          +----------------+
          |     JOBS       |
          +----------------+
          | job_id (PK)    |
          | job_title      |
          | min_salary     |
          | max_salary     |
          +----------------+

          +----------------+
          |   CUSTOMERS    |
          +----------------+
          | customer_id (PK)|
          | first_name      |
          | last_name       |
          | email           |
          | phone_number    |
          | address         |
          | city            |
          | state_province  |
          | postal_code     |
          | country_id (FK) |
          +----------------+
                  |
                  | 1
                  |
                  v
          +----------------+                        +----------------+
          |    ORDERS      |                        |   CATEGORIES   |
          +----------------+                        +----------------+
          | order_id (PK)   |                       | category_id (PK)|
          | customer_id (FK)|                       | category_name   |
          | order_date      |                       | description     |
          | status          |                       +----------------+
          | total_amount    |                                |
          +----------------+                                | 1
                  |                                         |
                  | 1                                       v
                  |                                +----------------+
                  v                                |    PRODUCTS    |
          +----------------+                       +----------------+
          |  ORDER_ITEMS   |                       | product_id (PK) |
          +----------------+                       | product_name    |
          | order_id (FK)   |                      | description     |
          | product_id (FK) |<---------------------| list_price      |
          | quantity        |                      | category_id (FK)|
          | unit_price      |                      +----------------+
          +----------------+                                |
                                                           | 1
                                                           |
                                                           v
                                                  +----------------+
                                                  |   INVENTORY    |
                                                  +----------------+
                                                  | product_id (FK) |
                                                  | quantity        |
                                                  | warehouse_id    |
                                                  +----------------+
```

## Table Definitions

### Core Tables

#### REGIONS
```sql
CREATE TABLE regions (
    region_id NUMBER PRIMARY KEY,
    region_name VARCHAR2(25)
);
```

#### COUNTRIES
```sql
CREATE TABLE countries (
    country_id CHAR(2) PRIMARY KEY,
    country_name VARCHAR2(40),
    region_id NUMBER REFERENCES regions(region_id)
);
```

#### LOCATIONS
```sql
CREATE TABLE locations (
    location_id NUMBER PRIMARY KEY,
    street_address VARCHAR2(40),
    postal_code VARCHAR2(12),
    city VARCHAR2(30) NOT NULL,
    state_province VARCHAR2(25),
    country_id CHAR(2) REFERENCES countries(country_id)
);
```

#### DEPARTMENTS
```sql
CREATE TABLE departments (
    department_id NUMBER PRIMARY KEY,
    department_name VARCHAR2(30) NOT NULL,
    manager_id NUMBER,
    location_id NUMBER REFERENCES locations(location_id)
);
```

#### JOBS
```sql
CREATE TABLE jobs (
    job_id VARCHAR2(10) PRIMARY KEY,
    job_title VARCHAR2(35) NOT NULL,
    min_salary NUMBER,
    max_salary NUMBER
);
```

#### EMPLOYEES
```sql
CREATE TABLE employees (
    employee_id NUMBER PRIMARY KEY,
    first_name VARCHAR2(20),
    last_name VARCHAR2(25) NOT NULL,
    email VARCHAR2(25) NOT NULL UNIQUE,
    phone_number VARCHAR2(20),
    hire_date DATE NOT NULL,
    job_id VARCHAR2(10) REFERENCES jobs(job_id),
    salary NUMBER,
    commission_pct NUMBER,
    manager_id NUMBER REFERENCES employees(employee_id),
    department_id NUMBER REFERENCES departments(department_id)
);
```

### Business Tables

#### CUSTOMERS
```sql
CREATE TABLE customers (
    customer_id NUMBER PRIMARY KEY,
    first_name VARCHAR2(20),
    last_name VARCHAR2(25) NOT NULL,
    email VARCHAR2(25),
    phone_number VARCHAR2(20),
    address VARCHAR2(40),
    city VARCHAR2(30),
    state_province VARCHAR2(25),
    postal_code VARCHAR2(12),
    country_id CHAR(2) REFERENCES countries(country_id)
);
```

#### CATEGORIES
```sql
CREATE TABLE categories (
    category_id NUMBER PRIMARY KEY,
    category_name VARCHAR2(50) NOT NULL,
    description VARCHAR2(400)
);
```

#### PRODUCTS
```sql
CREATE TABLE products (
    product_id NUMBER PRIMARY KEY,
    product_name VARCHAR2(50) NOT NULL,
    description VARCHAR2(400),
    list_price NUMBER(8,2),
    category_id NUMBER REFERENCES categories(category_id)
);
```

#### ORDERS
```sql
CREATE TABLE orders (
    order_id NUMBER PRIMARY KEY,
    customer_id NUMBER REFERENCES customers(customer_id),
    order_date DATE NOT NULL,
    status VARCHAR2(20),
    total_amount NUMBER(8,2)
);
```

#### ORDER_ITEMS
```sql
CREATE TABLE order_items (
    order_id NUMBER REFERENCES orders(order_id),
    product_id NUMBER REFERENCES products(product_id),
    quantity NUMBER(8,2) NOT NULL,
    unit_price NUMBER(8,2) NOT NULL,
    PRIMARY KEY (order_id, product_id)
);
```

#### INVENTORY
```sql
CREATE TABLE inventory (
    product_id NUMBER REFERENCES products(product_id),
    quantity NUMBER NOT NULL,
    warehouse_id NUMBER,
    PRIMARY KEY (product_id, warehouse_id)
);
```

### Reference Tables

#### CURRENCIES
```sql
CREATE TABLE currencies (
    currency_id VARCHAR2(3) PRIMARY KEY,
    currency_name VARCHAR2(25) NOT NULL,
    country_id CHAR(2) REFERENCES countries(country_id)
);
```

## Table Relationships

1. **One-to-Many Relationships**
   - One REGION has many COUNTRIES
   - One COUNTRY has many LOCATIONS
   - One LOCATION has many DEPARTMENTS
   - One DEPARTMENT has many EMPLOYEES
   - One JOB has many EMPLOYEES
   - One EMPLOYEE can manage many EMPLOYEES
   - One CUSTOMER can place many ORDERS
   - One ORDER can have many ORDER_ITEMS
   - One CATEGORY can have many PRODUCTS
   - One PRODUCT can be in many ORDER_ITEMS
   - One PRODUCT can have many INVENTORY records

2. **Many-to-One Relationships**
   - Many EMPLOYEES belong to one DEPARTMENT
   - Many EMPLOYEES have one JOB
   - Many EMPLOYEES report to one MANAGER (another EMPLOYEE)
   - Many LOCATIONS are in one COUNTRY
   - Many COUNTRIES are in one REGION

## Sample Queries

### Basic Joins

```sql
-- Find all employees with their department names
SELECT e.employee_id, e.first_name, e.last_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id
ORDER BY e.employee_id;

-- Find all departments with their locations and countries
SELECT d.department_id, d.department_name, l.city, c.country_name
FROM departments d
JOIN locations l ON d.location_id = l.location_id
JOIN countries c ON l.country_id = c.country_id
ORDER BY d.department_id;
```

### Hierarchical Queries

```sql
-- Display employee hierarchy (managers and their direct reports)
SELECT e.employee_id, e.first_name, e.last_name, 
       m.employee_id AS manager_id, m.first_name AS manager_first_name, 
       m.last_name AS manager_last_name
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.employee_id
ORDER BY m.employee_id NULLS FIRST, e.employee_id;
```

### Business Intelligence Queries

```sql
-- Sales by category
SELECT c.category_name, SUM(oi.quantity * oi.unit_price) AS total_sales
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
JOIN categories c ON p.category_id = c.category_id
JOIN orders o ON oi.order_id = o.order_id
WHERE o.order_date BETWEEN TO_DATE('2023-01-01', 'YYYY-MM-DD') 
                        AND TO_DATE('2023-12-31', 'YYYY-MM-DD')
GROUP BY c.category_name
ORDER BY total_sales DESC;

-- Top customers by order value
SELECT c.customer_id, c.first_name, c.last_name, 
       SUM(o.total_amount) AS total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.first_name, c.last_name
ORDER BY total_spent DESC
FETCH FIRST 10 ROWS ONLY;
```

## Data Dictionary Views

To explore the schema structure, you can use these queries:

```sql
-- List all tables
SELECT table_name
FROM user_tables
ORDER BY table_name;

-- List columns for a specific table
SELECT column_name, data_type, nullable, data_default
FROM user_tab_columns
WHERE table_name = 'EMPLOYEES'
ORDER BY column_id;

-- List constraints
SELECT constraint_name, constraint_type, table_name, search_condition
FROM user_constraints
WHERE table_name IN ('EMPLOYEES', 'DEPARTMENTS')
ORDER BY table_name, constraint_type;
```

## Notes on Sample Data

The sample database includes realistic data that represents:

- 4 regions
- 25 countries
- 10 locations
- 8 departments
- 10 job titles
- 50 employees
- 100 customers
- 8 product categories
- 50 products
- 200 orders with corresponding order items

This provides sufficient data volume for meaningful query practice while remaining manageable for learning purposes.
