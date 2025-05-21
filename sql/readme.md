-- ======================
-- DDL: Data Definition Language (MySQL)
-- ======================

-- Create Table
CREATE TABLE table_name (
    column1 datatype [constraint],
    column2 datatype [constraint],
    ...
);

-- Example:
CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    salary DECIMAL(10,2) CHECK (salary >= 0),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);

-- Alter Table
ALTER TABLE table_name ADD column_name datatype;
ALTER TABLE table_name MODIFY COLUMN column_name new_datatype;
ALTER TABLE table_name DROP COLUMN column_name;
ALTER TABLE table_name CHANGE old_column_name new_column_name datatype;

-- Drop Table
DROP TABLE table_name;

-- Truncate Table (removes all rows)
TRUNCATE TABLE table_name;

-- Rename Table
RENAME TABLE old_name TO new_name;

-- ======================
-- DML: Data Manipulation Language
-- ======================

-- Insert Data
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);

-- Update Data
UPDATE table_name
SET column1 = value1
WHERE condition;

-- Delete Data
DELETE FROM table_name
WHERE condition;

-- ======================
-- Constraints (MySQL)
-- ======================

-- NOT NULL
column_name datatype NOT NULL

-- UNIQUE
column_name datatype UNIQUE

-- PRIMARY KEY
column_name datatype PRIMARY KEY

-- FOREIGN KEY
FOREIGN KEY (column_name) REFERENCES other_table(column_name)

-- CHECK (MySQL 8.0+)
CHECK (column_name > 0)

-- DEFAULT
column_name datatype DEFAULT default_value

-- AUTO_INCREMENT
column_name INT AUTO_INCREMENT PRIMARY KEY

-- ======================
-- Constraint Manipulation (MySQL)
-- ======================

-- Add NOT NULL
ALTER TABLE table_name MODIFY column_name datatype NOT NULL;

-- Drop NOT NULL
ALTER TABLE table_name MODIFY column_name datatype NULL;

-- Add DEFAULT
ALTER TABLE table_name ALTER COLUMN column_name SET DEFAULT 'default_value';

-- Drop DEFAULT
ALTER TABLE table_name ALTER COLUMN column_name DROP DEFAULT;

-- Add UNIQUE Constraint
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE (column_name);

-- Drop UNIQUE Constraint
ALTER TABLE table_name DROP INDEX constraint_name;

-- Add PRIMARY KEY
ALTER TABLE table_name ADD CONSTRAINT constraint_name PRIMARY KEY (column_name);

-- Drop PRIMARY KEY
ALTER TABLE table_name DROP PRIMARY KEY;

-- Add FOREIGN KEY
ALTER TABLE table_name
ADD CONSTRAINT constraint_name FOREIGN KEY (column_name)
REFERENCES other_table(other_column);

-- Drop FOREIGN KEY
ALTER TABLE table_name DROP FOREIGN KEY constraint_name;

-- Add CHECK (MySQL 8.0+)
ALTER TABLE table_name
ADD CONSTRAINT constraint_name CHECK (column_name > 0);

-- Drop CHECK
ALTER TABLE table_name DROP CHECK constraint_name;

-- ======================
-- Keys
-- ======================

-- Primary Key
PRIMARY KEY (column_name)

-- Composite Key
PRIMARY KEY (col1, col2)

-- Foreign Key
FOREIGN KEY (column_name) REFERENCES other_table(column_name)

-- Unique Key
UNIQUE (column_name)

-- ======================
-- Aggregate Functions
-- ======================

SELECT
    COUNT(column_name),
    SUM(column_name),
    AVG(column_name),
    MIN(column_name),
    MAX(column_name)
FROM table_name
WHERE condition;

-- ======================
-- Operators in MySQL
-- ======================

-- Arithmetic: +, -, *, /, %
-- Comparison: =, != or <>, >, <, >=, <=
-- Logical: AND, OR, NOT
-- BETWEEN
SELECT * FROM table_name WHERE column BETWEEN val1 AND val2;

-- IN
SELECT * FROM table_name WHERE column IN (val1, val2, val3);

-- LIKE
SELECT * FROM table_name WHERE column LIKE 'A%';  -- Starts with A

-- IS NULL
SELECT * FROM table_name WHERE column IS NULL;

-- ======================
-- GROUPING & ORDERING
-- ======================

-- ORDER BY
SELECT * FROM table_name ORDER BY column_name ASC|DESC;

-- GROUP BY
SELECT column_name, COUNT(*) FROM table_name GROUP BY column_name;

-- HAVING
SELECT column_name, COUNT(*) FROM table_name GROUP BY column_name HAVING COUNT(*) > 1;

-- ======================
-- JOINS in MySQL
-- ======================

-- INNER JOIN
SELECT * FROM table1
INNER JOIN table2 ON table1.id = table2.foreign_id;

-- LEFT JOIN
SELECT * FROM table1
LEFT JOIN table2 ON table1.id = table2.foreign_id;

-- RIGHT JOIN
SELECT * FROM table1
RIGHT JOIN table2 ON table1.id = table2.foreign_id;

-- FULL OUTER JOIN (not supported directly in MySQL, use UNION)
SELECT * FROM table1
LEFT JOIN table2 ON table1.id = table2.id
UNION
SELECT * FROM table1
RIGHT JOIN table2 ON table1.id = table2.id;

-- ======================
-- UNION and ALIAS
-- ======================

-- UNION (removes duplicates)
SELECT column_name FROM table1
UNION
SELECT column_name FROM table2;

-- UNION ALL (includes duplicates)
SELECT column_name FROM table1
UNION ALL
SELECT column_name FROM table2;

-- Alias
SELECT column_name AS alias_name FROM table_name;
