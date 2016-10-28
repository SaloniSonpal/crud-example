##Description
Perform basic SQL Server CRUD operations from Node.js using [Tedious](https://github.com/tediousjs/tedious) connector.

##Pre-requisites
Lastest version of [Node.js](https://nodejs.org/en/download/) with the npm module.

##Setup

Create Project Directory
```bash
mkdir crud-example
cd crud-example
npm init -y
```

Install tedious and async module in your project folder
```bash
npm install tedious
npm install async
```

Create a Database that will be used by this app.
```sql
-- Create Database
CREATE DATABASE SampleDB;
GO

USE SampleDB;
GO

CREATE SCHEMA Company;
GO

-- Create Employee Table
CREATE TABLE Company.Employees (
  Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY,
  Name NVARCHAR(50),
  Location NVARCHAR(50)
);
GO

-- Insert a few employee records
INSERT INTO Company.Employees (Name, Location) VALUES
(N'Jared', N'Australia'),
(N'Nikita', N'India'),
(N'Tom', N'Germany');
GO

-- List the employees
SELECT * FROM Company.Employees;
GO
```

##Running the app

Copy contents of connect.js and crud.js into respectively into newly created files. Ensure you've updated the connection string with
```js
var config = {
  userName: 'login', // update me
  password: 'password', // update me
  server: '127.0.0.1',
  options: {
    database: 'SampleDB',
	  encrypt: true //required for Azure SQL Database
  }
```

In order to just test your connection to database run
```
node connect.js
```

A simple app crud.js performs inserts, updates, deletes, and selects data from the table.
```
node crud.js
```
