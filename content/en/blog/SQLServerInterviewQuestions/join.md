---
title: Combining Rows From Two Or More Tables Based On Related Columns
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 23
---

## Combining Rows From Two Or More Tables Based On Related Columns

- `JOIN` is combining rows from two or more tables based on related columns
- Type of join
    - `LEFT JOIN` (Left Outer Join)
        - Returns all rows from the left table and matched rows from the right table, filling with `NULL` if there's no match
    - `INNER JOIN` / `JOIN`
        - Returns matched rows in both tables
    - `RIGHT JOIN` (Right Outer Join)
        - Returns all rows from the right table and matched rows from the left table, filling with `NULL` if there's no match
    - `FULL JOIN` (Full Outer Join)
        - Returns all rows, filling with `NULL` where there is no match
    - `CROSS JOIN`
        - Returns the Cartesian product of rows from the tables in the join
        - Combining each row of the first table with each row of the second table
    - `SELF JOIN`
        - We can join a table to itself as if it were two separate tables

```sql
SELECT *
FROM table1_name
LEFT JOIN table2_name
ON table1_name.col_name = table2_name.col_name;

SELECT *
FROM table1_name
INNER JOIN table2_name
ON table1_name.col_name = table2_name.col_name;

SELECT *
FROM table1_name
RIGHT JOIN table2_name
ON table1_name.col_name = table2_name.col_name;

SELECT *
FROM table1_name
FULL JOIN table2_name
ON table1_name.col_name = table2_name.col_name;

SELECT *
FROM table1_name
CROSS JOIN table2_name;
-- we do not neeed join condition here

-- self join
SELECT *
FROM table1_name t1
INNER JOIN table1_name t2
ON t1.col1_name = t2.col2_name;
-- can be either an inner join, left join, or any other type of join
```

```sql
CREATE TABLE Customers (
    id INT IDENTITY(1, 1) PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE Orders (
    id INT IDENTITY(1, 1) PRIMARY KEY,
    customerId INT FOREIGN KEY REFERENCES Customers(id)
);

INSERT INTO Customers(name) VALUES ('Alice');
INSERT INTO Customers(name) VALUES ('Bob');
INSERT INTO Customers(name) VALUES ('Charlie');
INSERT INTO Orders(customerId) VALUES (1);
INSERT INTO Orders(customerId) VALUES (1);
INSERT INTO Orders(customerId) VALUES (2);
INSERT INTO Orders(customerId) VALUES (2);

| Customers |     | Orders |
| --------- | --- || --- | ---------- |
| id  | name    |  | id  | customerId |
| 1   | Alice   |  | 1   | 1          |
| 2   | Bob     |  | 2   | 1          |
| 3   | Charlie |  | 3   | 2          |
                   | 4   | 2          |

SELECT Customers.name AS CustomerName, Orders.id AS OrderID
FROM Customers
LEFT JOIN Orders
ON Customers.id = Orders.customerId;
/*
CustomerName  OrderID
Alice	        1
Alice	        2
Bob	          3
Bob	          4
Charlie	      NULL
*/

SELECT Orders.id AS OrderID, Customers.name AS CustomerName
FROM Orders
LEFT JOIN Customers
ON Orders.customerId = Customers.id;
/*
OrderID	 CustomerName
1	       Alice
2	       Alice
3	       Bob
4	       Bob
*/

SELECT Customers.name AS CustomerName, Orders.id AS OrderID
FROM Customers
INNER JOIN Orders
ON Customers.id = Orders.customerId;
/*
CustomerName  OrderID
Alice	        1
Alice	        2
Bob	          3
Bob	          4
*/

SELECT Orders.id AS OrderID, Customers.name AS CustomerName
FROM Orders
INNER JOIN Customers
ON Orders.customerId = Customers.id;
/*
OrderID	 CustomerName
1	       Alice
2	       Alice
3	       Bob
4	       Bob
*/

SELECT Customers.name AS CustomerName, Orders.id AS OrderID
FROM Customers
FULL JOIN Orders
ON Customers.id = Orders.customerId;
/*
CustomerName  OrderID
Alice	        1
Alice	        2
Bob	          3
Bob	          4
Charlie	      NULL
*/

SELECT Orders.id AS OrderID, Customers.name AS CustomerName
FROM Orders
FULL JOIN Customers
ON Orders.customerId = Customers.id;
/*
OrderID	 CustomerName
1	       Alice
2	       Alice
3	       Bob
4	       Bob
NULL     Charlie
*/
```

# [**175. Combine Two Tables**](https://leetcode.com/problems/combine-two-tables/)

```sql
/* Write your T-SQL query statement below */

SELECT p.firstName, p.lastName, a.city, a.state
FROM Person p
LEFT JOIN Address a
ON p.personId = a.personId;
```

# [**181. Employees Earning More Than Their Managers**](https://leetcode.com/problems/employees-earning-more-than-their-managers/)

```sql
/* Write your T-SQL query statement below */

SELECT e1.name AS [Employee]
FROM Employee e1
INNER JOIN Employee e2
ON e1.managerId = e2.id
WHERE e1.salary > e2.salary;
```

# [**183. Customers Who Never Order**](https://leetcode.com/problems/customers-who-never-order/)

```sql
/* Write your T-SQL query statement below */

SELECT c.name AS [Customers]
FROM Customers c
LEFT JOIN Orders o
ON c.id = o.customerId
WHERE o.id IS NULL;
```

# [**584. Find Customer Referee**](https://leetcode.com/problems/find-customer-referee/)

```sql
/* Write your T-SQL query statement below */

SELECT c1.name
FROM Customer c1
LEFT JOIN Customer c2
ON c1.referee_id = c2.id
WHERE c1.referee_id != 2 OR c1.referee_id IS NULL;
```