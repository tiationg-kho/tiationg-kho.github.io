---
title: Constraint
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 7
---

## Constraint

- `PRIMARY EKY` Constraint
    - A unique identifier (single col or composite cols) for a record in a database table
    - Maintain ****entity integrity
    - Automatically creates a clustered index
    - **Identity column** is commonly used for primary key
        - Auto-Incrementing
        - Uniqueness and Not Null
        - No Manual Insertion
- `FOREIGN KEY` Constraint
    - Identifies a link between two tables
    - Maintain referential integrity
    - Referential Action
        - `ON DELETE CERTAIN_ACTION`
            - Determines the action for child row when parent row got deleted
        
        | Action      | Description                                                                                                                             |
        | ----------- | --------------------------------------------------------------------------------------------------------------------------------------- |
        | CASCADE     | Deletes child rows if the parent row is deleted                                                                                         |
        | SET NULL    | Sets child keys to NULL if the parent row is delete                                                                                     |
        | SET DEFAULT | Sets child keys to their default value if the parent row is deleted                                                                     |
        | NO ACTION   | 1. Default setting. 2. Prevents parent row deletion if any child rows reference it (will throw error). 3. Check reference before commit |
        | RESTRICT    | 1. Prevents parent row deletion if any child rows reference it (will throw error). 2. Check reference immediately                       |
- `UNIQUE` Constraint
    - Values must be unique and can have one `NULL` only
    - Maintain domain integrity
    - Automatically creates a non-clustered index
- `NOT NULL` Constraint
    - Values cannot be `NULL`
    - Maintain domain integrity
- `CHECK` Constraint
    - Specifies a condition to be satisfied
    - Maintain domain integrity
- `DEFAULT` Constraint
    - Provide a default value
    - Maintain domain integrity
- eg.
    
    ```sql
    CREATE TABLE Departments (
        ID INT IDENTITY(1,1) PRIMARY KEY,
        FullName VARCHAR(255) NOT NULL
    );
    GO
    
    CREATE TABLE Students (
        -- PRIMARY KEY Constraint
        ID INT IDENTITY(1,1) PRIMARY KEY,
    
        -- FOREIGN KEY Constraint
        DepartmentID INT FOREIGN KEY REFERENCES Departments(ID) ON DELETE CASCADE,
    
        -- UNIQUE Constraint
        Email VARCHAR(255) UNIQUE,
    
        -- NOT NULL Constraint
        FullName VARCHAR(255) NOT NULL,
    
        -- CHECK Constraint
        Age INT CHECK(Age >= 18),
    
        -- DEFAULT Constraint
        AdmissionDate DATE DEFAULT GETDATE()
    );
    GO
    ```