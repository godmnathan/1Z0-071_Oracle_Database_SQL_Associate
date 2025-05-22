# Sample Database Setup Guide

This guide will help you set up the sample database used throughout this Oracle SQL learning repository. The sample database models a fictional company called "TechCorp" with departments, employees, products, customers, and orders.

## Prerequisites

- Oracle Database 19c or later installed (or access to an Oracle Cloud instance)
- SQL*Plus or another SQL client tool
- Basic knowledge of database administration

## Setup Options

### Option 1: Quick Setup (Recommended)

Run the automated setup script which will create all tables, constraints, and load sample data:

```bash
cd setup/scripts
sqlplus system/your_password@localhost:1521/ORCLPDB1 @setup_all.sql
```

### Option 2: Manual Setup

If you prefer to understand each step of the setup process, follow these instructions:

#### 1. Create the TechCorp User

Connect to your Oracle database as a user with administrative privileges:

```bash
sqlplus system/your_password@localhost:1521/ORCLPDB1
```

Run the following commands to create a new user and grant necessary privileges:

```sql
-- Create user
CREATE USER techcorp IDENTIFIED BY techcorp_password;

-- Grant privileges
GRANT CONNECT, RESOURCE, CREATE VIEW, CREATE SYNONYM TO techcorp;
GRANT UNLIMITED TABLESPACE TO techcorp;

-- Exit system user
EXIT
```

#### 2. Connect as TechCorp User

```bash
sqlplus techcorp/techcorp_password@localhost:1521/ORCLPDB1
```

#### 3. Create Tables

Run the table creation script:

```sql
@scripts/create_tables.sql
```

#### 4. Create Constraints

Run the constraints creation script:

```sql
@scripts/create_constraints.sql
```

#### 5. Load Sample Data

Run the data loading script:

```sql
@scripts/load_data.sql
```

## Database Schema

The TechCorp sample database includes the following tables:

### Core Tables

- **DEPARTMENTS**: Company departments
- **EMPLOYEES**: Employee information
- **JOBS**: Job titles and salary ranges
- **LOCATIONS**: Office locations
- **REGIONS**: Geographic regions

### Business Tables

- **CUSTOMERS**: Customer information
- **PRODUCTS**: Product catalog
- **CATEGORIES**: Product categories
- **ORDERS**: Customer orders
- **ORDER_ITEMS**: Items within orders
- **INVENTORY**: Product inventory levels

### Reference Tables

- **COUNTRIES**: Country information
- **CURRENCIES**: Currency codes and names

## Entity-Relationship Diagram

See the [Database Schema Diagram](database_schema.md) for a visual representation of the tables and their relationships.

## Verification

To verify your setup was successful, run the following query:

```sql
SELECT table_name 
FROM user_tables 
ORDER BY table_name;
```

You should see all the tables listed above.

Then check that sample data was loaded correctly:

```sql
SELECT COUNT(*) FROM employees;
SELECT COUNT(*) FROM departments;
SELECT COUNT(*) FROM products;
SELECT COUNT(*) FROM customers;
SELECT COUNT(*) FROM orders;
```

## Troubleshooting

### Common Issues

1. **ORA-01017: invalid username/password; logon denied**
   - Double-check your username and password
   - Ensure the user was created successfully

2. **ORA-01031: insufficient privileges**
   - Make sure you granted all necessary privileges to the techcorp user

3. **ORA-00942: table or view does not exist**
   - Verify you're connected as the techcorp user
   - Check if the table creation script ran successfully

### Getting Help

If you encounter issues not covered here:

1. Check the [Issues](https://github.com/godmnathan/1Z0-071_Oracle_Database_SQL_Associate/issues) page to see if others have reported similar problems
2. Create a new issue with details about your environment and the specific error

## Reset Database

If you need to start over, run the cleanup script:

```sql
@scripts/cleanup.sql
```

Then repeat the setup process.

## Next Steps

Once your database is set up:

1. Explore the [Database Schema Diagram](database_schema.md) to understand the data model
2. Try running some basic queries from the [Retrieving Data](../topics/002-retrieving-data/select-basics.md) section
3. Begin following the [Learning Path](../learning_path.md)

---

<p align="center">
  <b>Happy querying!</b>
</p>
