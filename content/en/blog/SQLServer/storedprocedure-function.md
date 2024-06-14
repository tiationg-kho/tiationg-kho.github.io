---
title: Stored Procedure vs Function
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 11
---

## Stored Procedure vs Function

| Feature                | Stored Procedure                                                                                                                                             | Function                                                          |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------- |
| Usage                  | Use for complex processing (involve DML, transaction and exception handling)                                                                                 | Use for computations                                              |
| Database Modifications | Yes (INSERT, UPDATE, DELETE)                                                                                                                                 | No                                                                |
| Syntax                 | Use EXEC to run                                                                                                                                              | Used in SELECT statement                                          |
| Parameters             | Input, output, input/output                                                                                                                                  | Input only                                                        |
| Return Type            | 1. Without RETURN, automatically implicit return a scalar value. 2. With RETURN, return a scalar value. 3. Without RETURN, use SELECT to return a result set | Must return a value, which can be a scalar value or a table value |
| Call each other        | Can call function                                                                                                                                            | Cannot call stored procedure                                      |

## Stored Procedure

```sql
CREATE PROCEDURE UpdateUserEmail
    @UserID INT,
    @NewEmail VARCHAR(255)
AS
BEGIN
    UPDATE Users
    SET Email = @NewEmail
    WHERE ID = @UserID;
END;
GO

EXEC UpdateUserEmail @UserID = 1, @NewEmail = 'newemail@example.com';
```

```sql
CREATE PROCEDURE GetUserName
    @UserID INT,
    @UserName VARCHAR(100) OUTPUT
AS
BEGIN
    SELECT @UserName = Name FROM Users WHERE ID = @UserID);
END;
GO

DECLARE @RetrievedUserName VARCHAR(100);
EXEC GetUserName @UserID = 1, @UserName = @RetrievedUserName OUTPUT;
```

## Function

```sql
CREATE FUNCTION CalculateArea(@radius FLOAT)
RETURNS FLOAT
AS
BEGIN
    DECLARE @area FLOAT;
    SET @area = PI() * @radius * @radius;
    RETURN @area;
END;
GO

SELECT CalculateArea(10) AS Area;
```

# [**177. Nth Highest Salary**](https://leetcode.com/problems/nth-highest-salary/)

```sql
CREATE FUNCTION getNthHighestSalary(@N INT)
RETURNS INT
AS
BEGIN
    DECLARE @res INT;

    WITH cte AS (
        SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS [rank]
        FROM Employee
    )
    SELECT @res = 
        MAX(salary)
        FROM cte
        WHERE [rank] = @N;
    
    RETURN @res;
END
```