# SQLnotes
My study notes of SQL
## DDL commands
In SQL, DDL means Data Definition Language. DDL commands are used to **create and modify the structure** of a database and database objects.
- **CREATE** - create objects (database, table, triggers etc)
```
CREATE TABLE [person]
(person_id SMALLINT IDENTITY(1,1) NOT NULL,
 fname VARCHAR(20) NOT NULL,
 lname VARCHAR(20) NOT NULL,
 gender VARCHAR(20) CHECK(gender in ('M','F')),
 birth_date DATE NOT NULL,
 street VARCHAR(30) NOT NULL,
 city VARCHAR(30) NOT NULL,
 state VARCHAR(30) NOT NULL,
 country VARCHAR(30) NOT NULL,
 postal_code VARCHAR(20) NOT NULL,
 CONSTRAINT pk_person PRIMARY KEY (person_id)
); 
```
- **DROP** - delete objects
```
DROP TABLE [person]
```
- **ALTER** - Used to alter the existing database or its objects structures.
```
%add new column to a table
ALTER TABLE [person]
ADD Education VARCHAR (50) NULL
%delete a column
ALTER TABLE [person]
DROP COLUMN state
%change variable type of a column
ALTER TABLE [person]
ALTER COLUMN [postal_code] VARCHAR(30) NULL
```
- **TRUNCATE** – Removes records from tables
```
TRUNCATE TABLE Database_Name.Schema_Name.Table_Name
```
- **RENAME** - Renaming the database objects
```
SP_RENAME '[Old Table Name]', '[New Table Name]'
```
## DML commands
DML means Data Manipulation Language. As its name suggests, these commands will perform data manipulation manipulate data presented in the server).
- SELECT - Select records or data from a table
```
SELECT * FROM person
SELECT city FROM person
```
- INSERT - Insert data into a database table
```
% specific columns
INSERT INTO [dbo].[SQL Insert] (
	[FirstName], [LastName], [Occupation])
VALUES ('Peter', 'Park', 'SpiderMan')
% all columns
INSERT INTO [dbo].[SQL Insert] 
VALUES ('SQL', 'Programming', 'Database', 50000, 1800)
% multi columns
INSERT INTO [dbo].[SQL Insert] 
VALUES ('Imran', 'Khan', 'Skilled Professional', 15900, 100)
      ,('Doe', 'Lara', 'Management', 15000, 60)
      ,('Ramesh', 'Kumar', 'Professional', 65000, 630)
```
- UPDATE -  Update existing records within a table
```
% update the yearly income of all the Employees to 100000
UPDATE [SQL Update]
SET [YearlyIncome] = 100000

% update one single record in [SQL Update] Table
UPDATE [SQL Update]
SET [YearlyIncome] = 250000
WHERE [EmpId] = 5

% update multiple records into [SQL Update] Table.
UPDATE [SQL Update]
SET [YearlyIncome] = 123456,
    [Sales] = 4500
WHERE [Occupation] = 'Professional'

UPDATE [SQL Update]
SET [Sales] = [Sales] * 2

% update the record in [SQL Update] Table with the new values in a [SQL Updates] Table.
UPDATE [SQL Update]
SET [YearlyIncome] = ( 
			SELECT [YearlyIncome] FROM [SQL Updates]
			WHERE [SQL Update].[FirstName] = [SQL Updates].[FirstName]
			AND 
			[SQL Update].[LastName] = [SQL Updates].[LastName])
```
- DELETE - delete one or more existing records from a table
```
% delete single record
DELETE FROM [SQL Delete]
  WHERE [EmpID] = 2
  
% SQL Delete Multiple records
USE [SQL Tutorial]
GO
DELETE del
FROM [SQL Delete] AS del
INNER JOIN
      Department AS dept ON
	 del.[DeptID] = dept.id
WHERE dept.DepartmentName = 'Sr. Software Developer'

USE [SQL Tutorial]
GO
DELETE FROM [SQL Delete]
WHERE [DeptID] IN
	(
	  SELECT id FROM Department
	    WHERE DepartmentName = 'Module Lead'
	)

% delete all columns
USE [SQL Tutorial]
GO
DELETE FROM [SQL Delete]
```
## DCL commands
DCL means Data Control Language. These commands will control the Data access permission. 
- GRANT – It gives users permission o access database.
- REVOKE – This command will withdraw the permission given by GRANT to access the database.
## TCL commands
- COMMIT – This will commit the running transaction
```
USE [SQL Tutorial]
GO

BEGIN TRAN

INSERT INTO [dbo].[EmployeeRecords] (
	         [EmpID], [FirstName], [LastName], [Education], [Occupation], [YearlyIncome], [Sales])
SELECT TOP 4 [EmpID], [FirstName], [LastName], [Education], [Occupation], [YearlyIncome], [Sales]
FROM [dbo].[Employee]

COMMIT TRANSACTION
```
- ROLLBACK – Rollback the current transaction 
- SAVEPOINT – You can set a save point so that, next time it will start from here
- SET TRANSACTION – Specify the transactions characteristics 
