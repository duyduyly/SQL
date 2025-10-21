# 🧱 Data Definition Language (DDL)

- DDL (Data Definition Language) is the part of SQL used to create, modify, and delete the structure of database objects — such as tables, schemas, indexes, and views.
- 👉 DDL changes the schema of the database (not the data inside it).
- Common DDL commands include:
- 
  | Command    | Description                                                                           |
  |------------|---------------------------------------------------------------------------------------|
  | `CREATE`   | Create new database objects (tables, views, indexes, schemas, etc.)                   |
  | `ALTER`    | Modify an existing database object (add/remove columns, change types, rename columns) |
  | `DROP`     | Delete objects permanently (tables, views, etc.)                                      |
  | `TRUNCATE` | Remove all rows from a table but keep the structure                                   |
  | `RENAME`   | Rename database objects (like tables or columns)                                      |

#
### 🧩 1. `CREATE` — Create Database Objects
- You use CREATE to define `new objects` in your database.
  - Tables
  - Schemas
  - Indexes
  - Databases
  - Views
  - etc.
#### Example:
```sql
-- Create a database
CREATE DATABASE company_db;

-- Create a schema (namespace for tables)
CREATE SCHEMA hr;

-- Create a table
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    salary DECIMAL(10, 2),
    hire_date DATE
);

-- Create an index for faster searching
CREATE INDEX idx_salary ON employees(salary);
```

#
### 🧩2. `ALTER` — Modify Structure of Objects
- Used when you need to add, remove, or modify columns or constraints in an existing table.
```sql
-- Add a new column
ALTER TABLE employees ADD department VARCHAR(50);

-- Modify column data type
ALTER TABLE employees ALTER COLUMN salary TYPE DECIMAL(12, 2);

-- Rename a column
ALTER TABLE employees RENAME COLUMN department TO dept_name;

-- Drop a column
ALTER TABLE employees DROP COLUMN dept_name;

```

#
### 🧩3. `DROP` — Delete Database Objects
- Removes a table, view, or database completely (structure + data).
- ⚠️ Be careful — once dropped, all data is lost (unless you have a backup).
- You can imagine , in the morning you open database and drop database, you will wake up right now haha :)) .
####  Example:
```sql 
-- Drop a table
DROP TABLE employees;

-- Drop a database
DROP DATABASE company_db;

-- Drop an index
DROP INDEX idx_salary;

-- Drop column
ALTER TABLE table_name
DROP COLUMN column_name;
```
- ❌ Remove Structure completely


#### Use drop remove table have relationship with other table.


#
### 🧩4. `TRUNCATE` — Remove All Data Quickly
- Deletes all rows from a table but keeps the structure so you can reuse it.
- It’s faster than DELETE because it doesn’t log individual row deletions.

#### Example:
```sql
TRUNCATE TABLE employees;
```
- ✅ Structure remains
- ❌ Data is gone


#
### 🧩5. `RENAME` — Rename Database Objects
- Used to rename tables, columns, or other database objects.
- Alter can update include:
  - Rename table
  - Rename column
  - Rename index
  - Add new column
  - Add new constraint
  - change column data type
  - add foreign key.
  - etc.

#### Example:
```sql
-- Rename table
ALTER TABLE employees RENAME TO staff;

-- Rename column (syntax may vary by DB)
ALTER TABLE staff RENAME COLUMN first_name TO fname;
```

### 🧠 Notes about DDL:
- Most DDL commands are auto-committed — you can’t undo them with ROLLBACK.
- You need appropriate privileges to run DDL commands (e.g., CREATE, ALTER, DROP).
- DDL affects the structure/schema, while DML affects the data.