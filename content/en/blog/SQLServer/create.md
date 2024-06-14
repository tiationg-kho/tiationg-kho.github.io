---
title: Create Database And Tables And Insert Data
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 13
---

## Create Database And Tables And Insert Data

```sql
--  Create Database
CREATE DATABASE MyDb; 
GO

-- Specify Database
USE MyDb; 
GO

--  Create Table
CREATE TABLE Departments (
    ID INT IDENTITY(1,1) PRIMARY KEY,
    FullName VARCHAR(255) NOT NULL
);
GO

--  Create Table
CREATE TABLE Students (
    ID INT IDENTITY(1,1) PRIMARY KEY,
    DepartmentID INT FOREIGN KEY REFERENCES Departments(ID),
    Email VARCHAR(255) UNIQUE,
    FullName VARCHAR(255) NOT NULL,
    Age INT CHECK(Age >= 18),
    AdmissionDate DATE DEFAULT GETDATE()
);
GO

-- Insert data into Departments
INSERT INTO Departments (FullName) VALUES ('Computer Science');
INSERT INTO Departments (FullName) VALUES ('Mathematics');
INSERT INTO Departments (FullName) VALUES ('Physics');
GO

-- Insert data into Students
INSERT INTO Students (DepartmentID, Email, FullName, Age) VALUES (1, 'john.doe@email.com', 'John Doe', 22);
INSERT INTO Students (DepartmentID, Email, FullName, Age) VALUES (1, 'jane.smith@email.com', 'Jane Smith', 24);
INSERT INTO Students (DepartmentID, Email, FullName, Age) VALUES (2, 'alice.johnson@email.com', 'Alice Johnson', 18);
INSERT INTO Students (DepartmentID, Email, FullName, Age) VALUES (3, 'bob.brown@email.com', 'Bob Brown', 21);
GO
```