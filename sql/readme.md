# 📘 MySQL Basic Syntax Cheat Sheet

---

## 🗄️ Database Operations

```sql
-- Create a database
CREATE DATABASE database_name;

-- Use a database
USE database_name;

-- Delete a database
DROP DATABASE database_name;
```

---

## 📋 Table Operations

```sql
-- Create a table
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);

-- View the structure of a table
DESCRIBE table_name;

-- Rename a table
RENAME TABLE old_name TO new_name;

-- Delete a table
DROP TABLE table_name;
```

---

## 📝 Data Manipulation

### 🔹 Insert Data

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### 🔹 Select Data

```sql
SELECT column1, column2 FROM table_name;

-- Select all columns
SELECT * FROM table_name;

-- With a condition
SELECT * FROM table_name WHERE condition;
```

### 🔹 Update Data

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

### 🔹 Delete Data

```sql
DELETE FROM table_name WHERE condition;
```

---

## 🔍 Conditions and Clauses

```sql
-- WHERE clause
SELECT * FROM table_name WHERE column = value;

-- ORDER BY
SELECT * FROM table_name ORDER BY column ASC|DESC;

-- LIMIT
SELECT * FROM table_name LIMIT number;

-- LIKE for pattern matching
SELECT * FROM table_name WHERE column LIKE 'pattern%';

-- IN clause
SELECT * FROM table_name WHERE column IN (value1, value2, ...);

-- BETWEEN
SELECT * FROM table_name WHERE column BETWEEN value1 AND value2;
```

---

## 🔗 Joins

```sql
-- INNER JOIN
SELECT * FROM table1
INNER JOIN table2 ON table1.column = table2.column;

-- LEFT JOIN
SELECT * FROM table1
LEFT JOIN table2 ON table1.column = table2.column;

-- RIGHT JOIN
SELECT * FROM table1
RIGHT JOIN table2 ON table1.column = table2.column;
```

---

## 🔐 User and Privileges

```sql
-- Create a user
CREATE USER 'username'@'host' IDENTIFIED BY 'password';

-- Grant privileges
GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'host';

-- Apply changes
FLUSH PRIVILEGES;
```

---

## 📌 Constraints

Constraints help maintain data accuracy and integrity in the database.

- `NOT NULL`: Prevents NULL values.
- `UNIQUE`: Ensures all values in a column are different.
- `PRIMARY KEY`: Combines `NOT NULL` and `UNIQUE`. Only one per table.
- `FOREIGN KEY`: Enforces referential integrity.
- `CHECK`: Ensures data meets a condition.
- `DEFAULT`: Sets a default value.

---

## 🏗️ Adding Constraints During Table Creation

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    age INT CHECK (age >= 18),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
);
```

---

## ➕ Adding Constraints to Existing Tables

```sql
-- Add a Primary Key
ALTER TABLE employees
ADD PRIMARY KEY (emp_id);

-- Add a Unique Constraint
ALTER TABLE employees
ADD CONSTRAINT unique_email UNIQUE (email);

-- Add a Check Constraint
ALTER TABLE employees
ADD CONSTRAINT check_age CHECK (age >= 18);

-- Add a Foreign Key
ALTER TABLE employees
ADD CONSTRAINT fk_dept
FOREIGN KEY (department_id) REFERENCES departments(department_id);
```

---

## ❌ Dropping Constraints

```sql
-- Drop Primary Key
ALTER TABLE employees
DROP PRIMARY KEY;

-- Drop Unique Constraint
ALTER TABLE employees
DROP INDEX unique_email;

-- Drop Check Constraint (MySQL 8.0+)
ALTER TABLE employees
DROP CHECK check_age;

-- Drop Foreign Key
ALTER TABLE employees
DROP FOREIGN KEY fk_dept;
```

---

## 📎 Notes on Foreign Keys

- Foreign keys must reference a column that is a `PRIMARY KEY` or `UNIQUE`.
- Both tables must use the same storage engine (InnoDB is required).
- Data types of both columns must match or be compatible.
