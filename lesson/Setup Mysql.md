# Setup Mysql 

## With 
## Install Mysql on MacOS
- Link: https://dev.mysql.com/downloads/mysql/

- Setup mysql password after download
  - ![setup-mysql-password.png](../resources/setup/setup-mysql-password.png)
- Download Mysql Workbench (GUI tool)
  - Link: https://dev.mysql.com/downloads/workbench/
- Start Mysql server
  - ![mysql-workbench-local-instance.png](../resources/setup/mysql-workbench-local-instance.png)

- Login
  - ![login-mysql-workbench.png](../resources/setup/login-mysql-workbench.png)
- After login success
- ![mysql-workbench-dashboard.png](../resources/setup/mysql-workbench-dashboard.png)

- you can try create database
```sql
CREATE DATABASE helloworld;
       
DROP DATABASE helloworld;
     
CREATE DATABASE school;

use school;
    
create table students (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

![mysql-example-table.png](../resources/setup/mysql-example-table.png)