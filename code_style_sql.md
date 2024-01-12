# SQL Code Style Guide

This document outlines the SQL code style and best practices to be followed in the [Project Name] repository. Consistency in SQL code style enhances readability and maintainability.

## Table of Contents

1. [Naming Conventions](#naming-conventions)
2. [Formatting](#formatting)
3. [Indentation](#indentation)
4. [Comments](#comments)
5. [Use of Aliases](#use-of-aliases)
6. [Joins](#joins)
7. [Subqueries](#subqueries)
8. [Data Modification Statements](#data-modification-statements)
9. [Stored Procedures and Functions](#stored-procedures-and-functions)
10. [Miscellaneous](#miscellaneous)

## Naming Conventions

- Use clear, descriptive names for tables, columns, and other database objects.
- Avoid using reserved keywords as identifiers; if necessary, enclose them in double quotes (e.g., `"select"`).

```sql
-- Good
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    username VARCHAR(255)
);

-- Bad - Using a reserved keyword
CREATE TABLE "select" (
    id INT PRIMARY KEY,
    name VARCHAR(255)
);
```

## Formatting
Write SQL keywords in uppercase for better readability.
Use consistent casing for identifiers (e.g., all lowercase or camelCase).

```sql
-- Good
SELECT column1, column2
FROM my_table
WHERE condition = 'example';

-- Bad - Inconsistent casing
Select column1, Column2
From my_table
Where condition = 'example';
```

## Indentation
Indent code consistently to improve readability.
Use a consistent number of spaces for indentation (e.g., 4 spaces).

```sql
-- Good
SELECT
    column1,
    column2
FROM
    my_table
WHERE
    condition = 'example';

-- Bad - Inconsistent indentation
SELECT
 column1,
    column2
FROM
my_table
 WHERE
condition = 'example';
```

## Comments
Add comments to explain complex queries, optimization choices, or any non-trivial logic.
Keep comments concise and updated.

```sql
-- Good
-- Calculate the total revenue for each product
SELECT
    product_id,
    SUM(revenue) AS total_revenue
FROM
    sales
GROUP BY
    product_id;

-- Bad - Vague comment
-- Query for products
SELECT * FROM products;
```

## Use of Aliases
Use aliases for table and column names, especially in complex queries.
Keep aliases short but meaningful.

```sql
-- Good
SELECT
    u.user_id,
    u.username,
    r.role_name
FROM
    users u
JOIN
    roles r ON u.role_id = r.role_id;

-- Bad - No use of aliases
SELECT
    users.user_id,
    users.username,
    roles.role_name
FROM
    users
JOIN
    roles ON users.role_id = roles.role_id;
```

## Joins
Explicitly specify the type of join (e.g., INNER JOIN, LEFT JOIN).
Use the ON keyword for join conditions.

```sql
-- Good
SELECT
    orders.order_id,
    customers.customer_name
FROM
    orders
JOIN
    customers ON orders.customer_id = customers.customer_id;

-- Bad - Implicit join
SELECT
    orders.order_id,
    customers.customer_name
FROM
    orders, customers
WHERE
    orders.customer_id = customers.customer_id;
```

## Subqueries
Use subqueries judiciously and format them for readability.
Ensure that subqueries are efficient and don't introduce unnecessary complexity.

```sql
-- Good
SELECT
    employee_id,
    employee_name
FROM
    employees
WHERE
    department_id = (
        SELECT
            department_id
        FROM
            departments
        WHERE
            department_name = 'HR'
    );

-- Bad - Unnecessary complexity
SELECT
    employee_id,
    employee_name
FROM
    employees
WHERE
    department_id IN (SELECT department_id FROM departments WHERE department_name = 'HR');
```

## Data Modification Statements
Clearly specify conditions in UPDATE and DELETE statements to avoid unintended consequences.
Use transactions appropriately for complex or critical updates.

```sql
-- Good
UPDATE
    products
SET
    price = 20
WHERE
    category = 'Electronics';

-- Bad - Unintentional update
UPDATE
    products
SET
    price = 20;
```

## Stored Procedures and Functions
Use stored procedures and functions to encapsulate reusable logic.
Clearly document the purpose and usage of stored procedures and functions.

```sql
-- Good
CREATE PROCEDURE GetEmployeeDetails(IN employee_id INT)
BEGIN
    SELECT
        *
    FROM
        employees
    WHERE
        employee_id = employee_id;
END;

-- Bad - Lack of documentation
CREATE PROCEDURE BadProcedure(IN parameter INT)
BEGIN
    -- Implementation without comments or documentation
END;
```

## Miscellaneous
Avoid using SELECT * in production queries; explicitly list the columns.
Use proper indexing for performance optimization.
Regularly review and optimize queries for efficiency.
