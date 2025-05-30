# SQL
Stores and note about sql


## Overview
- [Relationship](#relationship)
    - [One To Many(1-n)](#one-to-many1-n)
    - [One To One(1-1)](#one-to-one1-1)
    - [Many To Many(n-n)](#many-to-manyn-n)


### Relationship
- #### 🔗One-to-Many(1-n)
📘 Meaning: One row in Table A relates to many rows in Table B.

__📦 Example:__
```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    total DECIMAL(10, 2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);
```
Explanation: Each order belongs to one customer, but a customer can have many orders.

#
- #### 🔗One-to-One(1-1)
📘 Meaning: Each row in Table A relates to exactly one row in Table B and vice versa.

__📦 Example:__
```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    username VARCHAR(50)
);

CREATE TABLE profiles (
    id INT PRIMARY KEY,
    user_id INT UNIQUE,
    bio TEXT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```
Explanation: Each profile must belong to one user, and the `UNIQUE` constraint ensures it's one-to-one.

#
- #### 🔗Many-to-Many(n-n)
📘 Meaning: Many rows in Table A relate to many rows in Table B.

__📦 Example:__
```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE courses (
    id INT PRIMARY KEY,
    title VARCHAR(100)
);

CREATE TABLE student_courses (
    student_id INT,
    course_id INT,
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (course_id) REFERENCES courses(id)
);
```
Explanation: `student_courses` is a join (junction) table that allows many-to-many mapping.

