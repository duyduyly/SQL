# Table Define.
- [**Basic Syntax**](#-basic-syntax)
- [**Common Data Types**](#-data-types)
  - [*Numeric Data Types*](#numeric-data-types-)
  - [*String (Character) Data Types*](#string-character-data-types)
  - [*Date and Time Data Types*](#-date-and-time-data-types)
  - [*Other (Special) Data Types*](#-other-special-data-types)
- [**Table Constraints**](#-table-constraints)
- [**Relationships Between Tables**](#-relationships-between-tables)
- [**Modifying and Deleting Tables**](#modifying-and-deleting-tables)

#
- A `table` is a structure in a database that stores data in rows and columns — just like an Excel sheet.
Each column has a data type (e.g., INT, VARCHAR), and each row represents one record.

### 🧩 Basic Syntax
```sql
CREATE TABLE table_name (
    column_name1 datatype constraint,
    column_name2 datatype constraint,
    ...
);

-- Example:
CREATE TABLE employees (
     id INT PRIMARY KEY,
     name VARCHAR(100) NOT NULL,
     age INT,
     salary DECIMAL(10,2),
     hire_date DATE
);
```

-----------------
<br/>


## 🧩 Data Types
### 📝Numeric Data Types 
| Type               | Description                                   | Example                        | Range / Size              |
|--------------------|-----------------------------------------------|--------------------------------|---------------------------|
| `TINYINT`          | Very small integer                            | 127 / -128                     | 1 byte                    |
| `SMALLINT`         | Small integer                                 | 32767 / -32768                 | 2 bytes                   |
| `MEDIUMINT`        | Medium integer                                | 8,388,607 / -8,388,608         | 3 bytes                   |
| `INT` or `INTEGER` | Standard integer                              | 2,147,483,647 / -2,147,483,648 | 4 bytes                   |
| `BIGINT`           | Large integer                                 | 9.22e18 / -9.22e18             | 8 bytes                   |
| `DECIMAL(M,D)`     | Exact fixed-point decimal                     | 123.45 (`DECIMAL(5,2)`)        | M digits, D after decimal |
| `NUMERIC(M,D)`     | Same as DECIMAL                               | —                              | —                         |
| `FLOAT`            | Approximate floating point (single precision) | 123.45                         | 4 bytes                   |
| `DOUBLE`           | Approximate floating point (double precision) | 123.4567                       | 8 bytes                   |
| `BIT(M)`           | Bit-field (0 or 1 values)                     | `b'101'`                       | Up to 64 bits             |


**Example Code:**
```sql
CREATE TABLE numeric_types_example (
    tiny_col      TINYINT,
    small_col     SMALLINT,
    medium_col    MEDIUMINT,
    int_col       INT,
    big_col       BIGINT,
    decimal_col   DECIMAL(8,2),
    numeric_col   NUMERIC(6,3),
    float_col     FLOAT,
    double_col    DOUBLE,
    bit_col       BIT(4)
);

INSERT INTO numeric_types_example VALUES (
     127,             -- tiny_col (max value for TINYINT)
     32000,           -- small_col
     8000000,         -- medium_col
     2000000000,      -- int_col
     9000000000000000,-- big_col
     12345.67,        -- decimal_col (8 digits, 2 decimals)
     12.345,          -- numeric_col (6 digits, 3 decimals)
     123.45,          -- float_col
     123456.789,      -- double_col
     b'1010'          -- bit_col (binary 1010)
 );

```

💡 Note:
- Use `DECIMAL` for `money` or exact values.
- Use `FLOAT` or `DOUBLE` for scientific / approximate calculations


#
### 📝String (Character) Data Types
| Type                | Description               | Example                  | Notes                                         |
|---------------------|---------------------------|--------------------------|-----------------------------------------------|
| `CHAR(n)`           | Fixed-length string       | `'ABC'`                  | Always stores exactly `n` characters (padded) |
| `VARCHAR(n)`        | Variable-length string    | `'Alice'`                | Most common; up to 65,535 bytes total         |
| `TINYTEXT`          | Very small text           | `'short text'`           | Up to 255 bytes                               |
| `TEXT`              | Large text                | `'a long article...'`    | Up to 65,535 bytes                            |
| `MEDIUMTEXT`        | Medium text               | `'more text...'`         | Up to 16 MB                                   |
| `LONGTEXT`          | Very large text           | `'very long content...'` | Up to 4 GB                                    |
| `BINARY(n)`         | Fixed-length binary       | `0xFFEEDD`               | For raw bytes                                 |
| `VARBINARY(n)`      | Variable-length binary    | —                        | For binary data                               |
| `TINYBLOB`          | Very small binary data    | —                        | Up to 255 bytes                               |
| `BLOB`              | Binary Large Object       | —                        | Up to 65,535 bytes                            |
| `MEDIUMBLOB`        | Medium binary data        | —                        | Up to 16 MB                                   |
| `LONGBLOB`          | Very large binary data    | —                        | Up to 4 GB                                    |
| `ENUM('A','B',...)` | One value from list       | `'A'` or `'B'`           | Up to 65,535 options                          |
| `SET('A','B',...)`  | Multiple values from list | `'A,B'`                  | Can store multiple allowed options            |

**Example Code:**
```sql
CREATE TABLE string_types_example (
    char_col        CHAR(5),
    varchar_col     VARCHAR(50),
    tinytext_col    TINYTEXT,
    text_col        TEXT,
    mediumtext_col  MEDIUMTEXT,
    longtext_col    LONGTEXT,
    binary_col      BINARY(5),
    varbinary_col   VARBINARY(10),
    tinyblob_col    TINYBLOB,
    blob_col        BLOB,
    mediumblob_col  MEDIUMBLOB,
    longblob_col    LONGBLOB,
    enum_col        ENUM('A', 'B', 'C'),
    set_col         SET('X', 'Y', 'Z')
);


INSERT INTO string_types_example VALUES (
    'Hello',                       -- CHAR(5)
    'This is a varchar example',   -- VARCHAR(50)
    'Tiny text here',              -- TINYTEXT
    'This is a normal TEXT value', -- TEXT
    'Medium text content...',      -- MEDIUMTEXT
    'Long text content example...',-- LONGTEXT
    B'10101',                      -- BINARY(5)
    0x48656C6C6F,                  -- VARBINARY(10) = 'Hello' in hex
    0x41,                          -- TINYBLOB = 'A'
    0x426C6F62,                    -- BLOB = 'Blob'
    0x4D656469756D,                -- MEDIUMBLOB = 'Medium'
    0x4C6F6E67426C6F62,            -- LONGBLOB = 'LongBlob'
    'B',                           -- ENUM('A','B','C')
    'X,Y'                          -- SET('X','Y','Z')
);
```

💡 Note:
- Use `VARCHAR` for names, emails, titles, etc.
- Use `TEXT` for large paragraphs.
- Use `ENUM` or `SET` for fixed options like `'male'`, `'female'`, `'other'`.


#
### 🧩 Date and Time Data Types
| Type        | Description              | Example                 | Range                   |
|-------------|--------------------------|-------------------------|-------------------------|
| `DATE`      | Date (YYYY-MM-DD)        | `'2025-10-28'`          | 1000-01-01 → 9999-12-31 |
| `TIME`      | Time (HH:MM:SS)          | `'14:30:00'`            | -838:59:59 → 838:59:59  |
| `DATETIME`  | Date and time            | `'2025-10-28 14:30:00'` | 1000-01-01 → 9999-12-31 |
| `TIMESTAMP` | Date and time (auto UTC) | `'2025-10-28 14:30:00'` | 1970-01-01 → 2038-01-19 |
| `YEAR`      | Year only                | `'2025'`                | 1901 → 2155             |

**Example Code:**
```sql
CREATE TABLE datetime_types_example (
    date_col       DATE,
    time_col       TIME,
    datetime_col   DATETIME,
    timestamp_col  TIMESTAMP,
    year_col       YEAR
);


INSERT INTO datetime_types_example VALUES (
  '2025-10-28',             -- DATE (YYYY-MM-DD)
  '14:30:00',               -- TIME (HH:MM:SS)
  '2025-10-28 14:30:00',    -- DATETIME (YYYY-MM-DD HH:MM:SS)
  '2025-10-28 14:30:00',    -- TIMESTAMP (auto UTC)
  '2025'                    -- YEAR (YYYY)
);
```

💡 Note:
- Use `DATETIME` for general purposes.
- Use `TIMESTAMP` for auto-updated or __timezone-aware__ columns (e.g., record creation time).



#
### 🧩 Other (Special) Data Types
| Type                                         | Description                  | Example                          |
|----------------------------------------------|------------------------------|----------------------------------|
| `JSON`                                       | Stores JSON data             | `'{"name": "Alice", "age": 25}'` |
| `GEOMETRY`, `POINT`, `LINESTRING`, `POLYGON` | For spatial data (maps, GIS) | —                                |

**Example Code:**
```sql
CREATE TABLE special_types_example (
    json_col        JSON,
    point_col       POINT,
    linestring_col  LINESTRING,
    polygon_col     POLYGON
);
INSERT INTO special_types_example VALUES (
     '{"name": "Alice", "age": 25}',                   -- JSON
     ST_GeomFromText('POINT(10 20)'),                  -- POINT (x, y)
     ST_GeomFromText('LINESTRING(0 0, 10 10, 20 25)'), -- LINESTRING
     ST_GeomFromText('POLYGON((0 0, 10 0, 10 10, 0 10, 0 0))')  -- POLYGON
 );
```

Read More: https://www.w3schools.com/mysql/mysql_datatypes.asp


-----------------
<br/>


## 🔹 Table Constraints
- `Constraints` are rules that you apply to columns in a table to ensure data integrity — they control what kind of data can be stored.
  
| Constraint         | Purpose                                                 | Example                                            |
|--------------------|---------------------------------------------------------|----------------------------------------------------|
| **PRIMARY KEY**    | Uniquely identifies each record in the table            | `id INT PRIMARY KEY`                               |
| **FOREIGN KEY**    | Links one table’s column to another table’s primary key | `FOREIGN KEY (dept_id) REFERENCES departments(id)` |
| **UNIQUE**         | Ensures all values in a column are different            | `email VARCHAR(100) UNIQUE`                        |
| **NOT NULL**       | Prevents a column from having NULL values               | `name VARCHAR(100) NOT NULL`                       |
| **CHECK**          | Ensures values meet a condition                         | `CHECK (age >= 18)`                                |
| **DEFAULT**        | Sets a default value if none is provided                | `status VARCHAR(10) DEFAULT 'active'`              |
| **AUTO_INCREMENT** | Automatically increases numeric values                  | `id INT AUTO_INCREMENT`                            |

**Example Code:**
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY AUTO_INCREMENT,          -- PRIMARY KEY + AUTO_INCREMENT
    emp_name VARCHAR(100) NOT NULL,                 -- NOT NULL
    email VARCHAR(100) UNIQUE,                      -- UNIQUE
    age INT CHECK (age >= 18),                      -- CHECK constraint
    salary DECIMAL(10,2) DEFAULT 0.00,              -- DEFAULT value
    dept_id INT,                                   -- FOREIGN KEY column
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)  -- FOREIGN KEY constraint
);

INSERT INTO employees (emp_name, email, age, salary, dept_id)
VALUES ('Alice', 'alice@example.com', 25, 5000.00, 1);


-- To enforce that column values must meet a specific condition (TRUE/FALSE expression).
CREATE TABLE students (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(100) NOT NULL,
  age INT CHECK (age >= 18),
  grade CHAR(1) CHECK (grade IN ('A', 'B', 'C', 'D', 'F'))
);

```

### Summary Table of Conditional Constraints
| Constraint       | Condition Type      | Example                            | Behavior                  |
|------------------|---------------------|------------------------------------|---------------------------|
| `CHECK`          | Logical condition   | `CHECK (age >= 18)`                | Enforces rule on values   |
| `DEFAULT`        | Fallback condition  | `DEFAULT 'active'`                 | Sets a value when missing |
| `NOT NULL`       | Must have a value   | `name VARCHAR(50) NOT NULL`        | Prevents `NULL`           |
| `UNIQUE`         | Must be different   | `email VARCHAR(100) UNIQUE`        | Avoids duplicates         |
| `PRIMARY KEY`    | Unique + Not Null   | `id INT PRIMARY KEY`               | One per table             |
| `FOREIGN KEY`    | Relationship rule   | `FOREIGN KEY (...) REFERENCES ...` | Enforces valid relations  |
| `AUTO_INCREMENT` | Conditional counter | `id INT AUTO_INCREMENT`            | Generates next number     |



💡 6️⃣ Tips & Best Practices
- ✅ Always define a PRIMARY KEY.
- ✅ Use FOREIGN KEY to link related tables.
- ✅ Apply NOT NULL where data is required.
- ✅ Use CHECK for logical rules like CHECK (salary > 0).
- ✅ Use DEFAULT for system-generated or common values.
- ✅ Use AUTO_INCREMENT for ID columns.

-----------------
<br/>

## 🧩 Relationships Between Tables
- **One-to-One (1-1)**: Each row in Table A relates to exactly one row in Table B.
- **One-to-Many (1-n)**: One row in Table A relates to many rows in Table B.
- **Many-to-Many (n-n)**: Many rows in Table A relate to many rows in Table B (usually via a junction table).
### Read Here [Mapping In SQL.md](Mapping%20In%20SQL.md)

-----------------
<br/>

## 🧩Modifying and Deleting Tables
// Add After.

-----------------
<br/>

## 💡 7. Best Practices

- ✅ Always use a primary key.
- ✅ Choose the right data type for efficiency.
- ✅ Use constraints to keep data clean.
- ✅ Use snake_case or lowercase for consistency.
- ✅ Add FOREIGN KEYS to keep relational integrity.