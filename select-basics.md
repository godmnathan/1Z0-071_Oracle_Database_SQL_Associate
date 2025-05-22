# SQL SELECT Statement Fundamentals

## Introduction to Data Retrieval

The SELECT statement is the cornerstone of SQL and data retrieval. It allows you to query and retrieve data from one or more tables in a database. Mastering the SELECT statement is essential for working with relational databases and forms the foundation for more complex SQL operations.

## Basic SELECT Statement Syntax

The most basic form of the SELECT statement is:

```sql
SELECT column1, column2, ...
FROM table_name;
```

This statement retrieves specified columns from the named table. Let's break down the components:

- **SELECT**: The keyword that indicates a query operation
- **column1, column2, ...**: The columns you want to retrieve
- **FROM**: The keyword that precedes the data source
- **table_name**: The table from which to retrieve data

### Example: Retrieving Specific Columns

```sql
SELECT employee_id, first_name, last_name
FROM employees;
```

This query returns the employee ID, first name, and last name for all employees in the employees table.

### Retrieving All Columns

To retrieve all columns from a table, use the asterisk (*) wildcard:

```sql
SELECT *
FROM departments;
```

While convenient for exploration, using the asterisk in production code is generally discouraged because:
- It retrieves unnecessary data, potentially impacting performance
- It makes code less maintainable if table structure changes
- It can lead to ambiguity in joins

Best practice is to explicitly list the columns you need.

## Column Aliases

Column aliases allow you to rename columns in the result set, making output more readable or meaningful.

### Basic Alias Syntax

```sql
SELECT column_name AS alias_name
FROM table_name;
```

### Examples

```sql
-- Using AS keyword
SELECT first_name AS name, last_name AS surname
FROM employees;

-- Omitting AS keyword (also valid)
SELECT first_name name, last_name surname
FROM employees;

-- Using quotes for aliases with spaces or special characters
SELECT first_name "First Name", last_name "Last Name"
FROM employees;
```

### Aliases in Expressions

Aliases are particularly useful when working with expressions:

```sql
SELECT employee_id, salary, salary * 1.1 AS increased_salary
FROM employees;
```

## Arithmetic Expressions

You can perform arithmetic operations in SELECT statements:

### Basic Operators

- Addition: `+`
- Subtraction: `-`
- Multiplication: `*`
- Division: `/`

### Examples

```sql
-- Calculate annual salary
SELECT employee_id, first_name, salary, salary * 12 AS annual_salary
FROM employees;

-- Calculate commission amount
SELECT employee_id, first_name, salary, commission_pct, 
       salary * commission_pct AS commission_amount
FROM employees
WHERE commission_pct IS NOT NULL;

-- Calculate net salary after tax
SELECT employee_id, first_name, salary, 
       salary - (salary * 0.2) AS net_salary
FROM employees;
```

### Operator Precedence

SQL follows standard mathematical operator precedence:
1. Parentheses
2. Multiplication and division (from left to right)
3. Addition and subtraction (from left to right)

```sql
-- Using parentheses to control precedence
SELECT employee_id, salary, 
       (salary + 1000) * 1.1 AS bonus_calculation
FROM employees;
```

## Literal Values

Literal values are fixed data items that can be included in SELECT statements:

### String Literals

String literals are enclosed in single quotes:

```sql
SELECT employee_id, first_name, 'Active' AS status
FROM employees;
```

### Numeric Literals

Numeric literals don't require quotes:

```sql
SELECT employee_id, first_name, salary, 500 AS bonus
FROM employees;
```

### Date Literals

Date literals are enclosed in single quotes and require proper formatting:

```sql
SELECT employee_id, first_name, hire_date, 
       '01-JAN-2023' AS review_date
FROM employees;
```

## Concatenation

The concatenation operator (`||`) combines columns or strings:

```sql
SELECT employee_id, first_name || ' ' || last_name AS full_name
FROM employees;
```

### Concatenation with Literal Values

```sql
SELECT employee_id, 
       'Employee: ' || first_name || ' ' || last_name AS employee_info
FROM employees;
```

### Alternative Quote Operator (q)

For strings containing quotes, you can use the alternative quote operator:

```sql
SELECT employee_id, first_name,
       q'[Employee's Department]' AS department_header
FROM employees;
```

## DISTINCT Keyword

The DISTINCT keyword eliminates duplicate values from the result set:

```sql
SELECT DISTINCT department_id
FROM employees;
```

### DISTINCT with Multiple Columns

When DISTINCT is used with multiple columns, it considers the combination of values:

```sql
SELECT DISTINCT department_id, job_id
FROM employees;
```

## Handling NULL Values

NULL represents an unknown, unavailable, or inapplicable value.

### Identifying NULL Values

```sql
SELECT employee_id, first_name, commission_pct
FROM employees
WHERE commission_pct IS NULL;
```

### Arithmetic with NULL Values

Any arithmetic operation involving NULL results in NULL:

```sql
SELECT employee_id, salary, commission_pct, 
       salary * commission_pct AS commission
FROM employees;
```

In this example, if `commission_pct` is NULL, the calculated `commission` will also be NULL.

### NVL Function

The NVL function substitutes a value when a NULL is encountered:

```sql
SELECT employee_id, salary, commission_pct, 
       salary * NVL(commission_pct, 0) AS commission
FROM employees;
```

## DUAL Table

DUAL is a special one-row, one-column table available to all users:

```sql
SELECT SYSDATE
FROM DUAL;
```

It's useful for:
- Evaluating expressions
- Calling functions
- Performing calculations not related to any table

```sql
-- Calculating values
SELECT 5 * 7
FROM DUAL;

-- Using functions
SELECT UPPER('oracle')
FROM DUAL;

-- Generating sequences
SELECT SEQUENCE_NAME.NEXTVAL
FROM DUAL;
```

## Best Practices for SELECT Statements

1. **Be Specific**: Always specify exactly which columns you need rather than using `SELECT *`

2. **Use Meaningful Aliases**: Choose clear, descriptive names for column aliases

3. **Format for Readability**: Use consistent indentation and line breaks for complex queries

4. **Comment Your Code**: Add comments to explain complex logic or business rules

5. **Handle NULL Values**: Always consider how NULL values might affect your results

6. **Test Edge Cases**: Verify your queries work correctly with empty tables, NULL values, and boundary conditions

7. **Consider Performance**: For large tables, be mindful of query efficiency and indexing

## Common Mistakes to Avoid

1. **Ignoring NULL Values**: Failing to account for NULL values in calculations

2. **Misusing DISTINCT**: Overusing DISTINCT can impact performance

3. **Ambiguous Column Names**: Not qualifying column names in multi-table queries

4. **Incorrect Data Type Handling**: Not properly converting between data types

5. **Poor Formatting**: Writing queries that are difficult to read and maintain

## Practice Exercises

1. Write a query to display the employee ID, full name (first name and last name separated by a space), job ID, and hire date for all employees.

2. Create a query that displays the employee ID, full name, and salary increased by 15%.

3. Write a query to display unique department IDs from the employees table.

4. Create a query that displays employee ID, salary, commission percentage, and the income after commission (salary + commission).

5. Write a query to display the current date from the DUAL table.

## Summary

The SELECT statement is fundamental to SQL and data retrieval. By mastering its basic syntax and features, you build the foundation for more complex queries and data analysis. Remember to be specific about the columns you select, use meaningful aliases, and handle NULL values appropriately.

---

## Additional Resources

- [Oracle SQL Language Reference](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/SELECT.html)
- [SQL SELECT Statement Interactive Tutorial](https://www.oracle.com/database/technologies/appdev/sql.html)
- [Oracle Live SQL](https://livesql.oracle.com/) - Practice environment for SQL queries
