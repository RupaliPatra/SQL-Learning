# SQL-Learning

********************************* Module 1: SQL Basics ********************************************

1. What is SQL?

Definition: SQL (Structured Query Language) is used to interact with databases.

SELECT 'Hello, SQL!';

2. Database

Definition: A database is a collection of organized data.

CREATE DATABASE school;

3. Table

Definition: A table stores data in rows and columns.

CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    age INT
);

4. Row & Column

Definition: A row is one record, and a column is one attribute.

INSERT INTO students VALUES (1, 'Rupali', 22);
SELECT * FROM students;

5. Primary Key

Definition: A unique identifier for each row.

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);

6. Foreign Key

Definition: Connects two related tables.

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES students(id)
);

7. DBMS vs RDBMS

Definition:

* DBMS: Stores data.
* RDBMS: Stores related data using tables and relationships.

⸻

Module 1 Practice

CREATE DATABASE school;
USE school;
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);
CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    student_id INT,
    course_name VARCHAR(50),
    FOREIGN KEY (student_id) REFERENCES students(id)
);
INSERT INTO students VALUES
(1, 'Rupali', 22),
(2, 'Sahil', 20);
SELECT * FROM students;

Concepts Used: Database, Table, Row & Column, Primary Key, Foreign Key.

⸻

******************************************** Module 2: Basic Queries ********************************************

8. SELECT

Definition: Retrieves data from a table.

SELECT * FROM students;

9. WHERE

Definition: Filters records.

SELECT * FROM students
WHERE age > 20;

10. ORDER BY

Definition: Sorts records.

SELECT * FROM students
ORDER BY age DESC;

11. DISTINCT

Definition: Removes duplicate values.

SELECT DISTINCT age
FROM students;

12. LIMIT

Definition: Limits the number of rows returned.

SELECT * FROM students
LIMIT 2;

⸻

Module 2 Practice

SELECT DISTINCT name, age
FROM students
WHERE age >= 20
ORDER BY age DESC
LIMIT 2;

Concepts Used: SELECT, WHERE, DISTINCT, ORDER BY, LIMIT.

⸻

******************************************** Module 3: Filtering ********************************************

13. AND

Definition: All conditions must be true.

SELECT * FROM students
WHERE age > 20 AND name = 'Rupali';

14. OR

Definition: At least one condition must be true.

SELECT * FROM students
WHERE age = 20 OR age = 22;

15. NOT

Definition: Reverses a condition.

SELECT * FROM students
WHERE NOT age = 20;

16. IN

Definition: Matches any value in a list.

SELECT * FROM students
WHERE age IN (20, 22);

17. BETWEEN

Definition: Selects values within a range.

SELECT * FROM students
WHERE age BETWEEN 20 AND 23;

18. LIKE

Definition: Searches using patterns.

SELECT * FROM students
WHERE name LIKE 'R%';

19. IS NULL

Definition: Finds NULL values.

SELECT * FROM students
WHERE age IS NULL;

⸻

Module 3 Practice

SELECT *
FROM students
WHERE age BETWEEN 20 AND 25
AND name LIKE 'R%'
AND age IS NOT NULL
OR age IN (19, 22);

Concepts Used: AND, OR, NOT, IN, BETWEEN, LIKE, IS NULL.

⸻

******************************************** Module 4: Functions ********************************************

20. COUNT()

Definition: Counts rows.

SELECT COUNT(*) FROM students;

21. SUM()

Definition: Adds values.

SELECT SUM(age) FROM students;

22. AVG()

Definition: Finds the average.

SELECT AVG(age) FROM students;

23. MAX()

Definition: Finds the highest value.

SELECT MAX(age) FROM students;

24. MIN()

Definition: Finds the lowest value.

SELECT MIN(age) FROM students;

⸻

Module 4 Practice

SELECT
COUNT(*) AS Total_Students,
SUM(age) AS Total_Age,
AVG(age) AS Average_Age,
MAX(age) AS Oldest,
MIN(age) AS Youngest
FROM students;

Concepts Used: COUNT(), SUM(), AVG(), MAX(), MIN().

⸻

******************************************** Module 5: Grouping ********************************************

25. GROUP BY

Definition: Groups rows with the same value.

SELECT age, COUNT(*)
FROM students
GROUP BY age;

26. HAVING

Definition: Filters grouped data.

SELECT age, COUNT(*)
FROM students
GROUP BY age
HAVING COUNT(*) > 1;

⸻

Module 5 Practice

SELECT age,
COUNT(*) AS Total
FROM students
GROUP BY age
HAVING COUNT(*) > 0;

Concepts Used: GROUP BY, HAVING.

⸻

******************************************** Module 6: Joins ********************************************

27. INNER JOIN

Definition: Returns matching records from both tables.

SELECT s.name, o.order_id
FROM students s
INNER JOIN orders o
ON s.id = o.student_id;

28. LEFT JOIN

Definition: Returns all rows from the left table and matching rows from the right table.

SELECT s.name, o.order_id
FROM students s
LEFT JOIN orders o
ON s.id = o.student_id;

29. RIGHT JOIN

Definition: Returns all rows from the right table and matching rows from the left table.

SELECT s.name, o.order_id
FROM students s
RIGHT JOIN orders o
ON s.id = o.student_id;

30. FULL JOIN

Definition: Returns all matching and non-matching rows.

SELECT s.name, o.order_id
FROM students s
FULL OUTER JOIN orders o
ON s.id = o.student_id;

31. SELF JOIN

Definition: Joins a table with itself.

SELECT A.name, B.name
FROM students A
JOIN students B
ON A.id <> B.id;

⸻

Module 6 Practice

SELECT
s.id,
s.name,
o.order_id,
o.course_name
FROM students s
LEFT JOIN orders o
ON s.id = o.student_id;

Concepts Used: INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN, SELF JOIN.

⸻

******************************************** Module 7: Advanced SQL ********************************************

32. Subqueries

Definition: A query inside another query.

SELECT name
FROM students
WHERE age = (
    SELECT MAX(age)
    FROM students
);

33. Views

Definition: A virtual table created from a query.

CREATE VIEW student_view AS
SELECT name, age
FROM students;

34. Indexes

Definition: Improves query performance.

CREATE INDEX idx_name
ON students(name);

⸻

Module 7 Practice

CREATE VIEW topper AS
SELECT *
FROM students
WHERE age = (
    SELECT MAX(age)
    FROM students
);
CREATE INDEX idx_student_name
ON students(name);
SELECT * FROM topper;

Concepts Used: Subqueries, Views, Indexes.
