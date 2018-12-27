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
