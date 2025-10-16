# SQL
- [**What is SQL**](#what-is-sql)
- [**What is Database and Schema**](#what-is-database-and-schema)
  - [*What is Database?*](#-what-is-the-database)
  - [*What is Schema?*](#-what-is-schema)
- [**Difference between SQL and NoSQL**](#difference-between-sql-and-nosql)
  - [*When use SQL?*](#-when-use-sql)
  - [*When use NoSQL?*](#-when-use-nosql-need-read-more)
- [**In reality, what use SQL for?**](#in-reality-what-use-sql-for)
- [**DDL (Data Definition Language) and DML (Data Manipulation Language) Commands**](#ddl-data-definition-language-and-dml-data-manipulation-language-commands)
  - [*DDL (Data Definition Language)*](#ddl-data-definition-language)
  - [*DML (Data Manipulation Language)*](#dml-data-manipulation-language)


## what is SQL?
- SQL (Structured Query Language) is a programming language designed for managing and manipulating relational databases. It allows users to create, read, update, and delete data stored in tables within a database.

--------------------
<br/>

## What is Database and Schema?
### 💡 What is the Database?
- A Database is structure collection of data - like digital filing cabinet.
- It stores information in an organized way, making it easily add, find, and manage it.

#
### 💡 What is Schema?
- A schema is the structure or blueprint of your database — it defines how your data is organized.
  You can think of it as a layout or plan describing
  - What tables exist
  - What columns each table has
  - What data types they store
  - Relationships between tables (keys, constraints, etc.)

#
### Summary:
- ✅ Database: The overall storage container for all your data.
- ✅ Schema: The structure and organization inside a database — grouping related tables and defining how they connect.

--------------------
<br/>

## Difference between SQL and NoSQL?
| Concept            | **SQL (Relational DB)**                                        | **NoSQL (Non-Relational DB)**                                                            |
|--------------------|----------------------------------------------------------------|------------------------------------------------------------------------------------------|
| **Structure**      | Tables (rows & columns)                                        | Collections (documents), key-value pairs, graphs, or wide-columns                        |
| **Schema**         | Fixed schema (must define columns before inserting data)       | Flexible schema (you can add fields anytime)                                             |
| **Query language** | SQL (standardized)                                             | Each database has its own query style (e.g. MongoDB uses JSON-like syntax)               |
| **Relationships**  | Great for complex relationships using **joins**                | Usually avoids joins; data often embedded                                                |
| **Transactions**   | Strong ACID guarantees (Atomic, Consistent, Isolated, Durable) | Some NoSQL DBs offer eventual consistency (faster, but not always immediate consistency) |
| **Scalability**    | Vertical (add more power to one server)                        | Horizontal (add more servers easily)                                                     |

#
### 💡 When use SQL?
#### Use SQL when:
- Data has a clear structure
- Relationships are important
- Transactions must be accurate
- You need complex queries
- You care about data integrity and strong consistency.

#
#### SQL Databases:
- MySQL (frequent use)
- PostgreSQL (frequent use)
- Microsoft SQL Server
- Oracle
- MariaDB


------------------------
<br/>

### 💡 When use NoSQL? (need Read More)
#### Use NoSQL when:
- Data is semi-structured or unstructured
- Schema changes often
- You need to scale massively
- High speed and flexibility matter more than strict structure.
- You don’t need complex joins

#
#### NoSQL Databases:
- MongoDB → Document store (most popular)
- Redis → Key-value store (super fast cache)
- Cassandra → Wide-column store (used by Netflix)
- Neo4j → Graph database (for relationships like social networks)



## In reality, what use SQL for?
- SQL is everywhere — here’s how it’s used in real life:
  1. `Web apps` – When you log in, order something online, or view your profile, the app uses SQL behind the scenes to get or save data.
    - Example: A shopping site runs `SELECT * FROM products WHERE category = 'shoes'`.
  2. `Finance & banking` – SQL is used to manage transactions, accounts, and histories safely and consistently.
  3. `Analytics / Business Intelligence (BI) – Analysts` use SQL to query millions of records to find patterns, make reports, and guide decisions.
  4. `Mobile apps` – Many apps store local data using SQLite, a lightweight SQL database.
  5. `Data science` / AI – SQL helps prepare and filter data before analysis or training models.


----------------
<br/>

## DDL (Data Definition Language) and DML (Data Manipulation Language) Commands
### DDL (Data Definition Language)
- DDL is used to define and manage the structure of the database — like creating tables, modifying them, or deleting them.
-  Common Keywords:
   - `CREATE TABLE` – to make a new table
   - `ALTER TABLE` – to change an existing table (add/remove columns)
   - `DROP TABLE` – to delete a table
   - `CREATE INDEX` – to speed up searches on a column
   - `DROP INDEX` – to remove an index

#
### DML (Data Manipulation Language)
- DML is used to work with the data inside those tables — inserting, reading, updating, or deleting rows.
- Common Keywords:
   - `SELECT` – to read data from a table
   - `INSERT INTO` – to add new rows
   - `UPDATE` – to change existing rows
   - `DELETE` – to remove rows