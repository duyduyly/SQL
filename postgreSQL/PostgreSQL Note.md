# PostgreSQL Note

- [**Import**](#import)
  - [*Import with .dump*](#import-with-dump)
  - [*import DB .sql (DB existed)*](#import-db-sql-db-existed)
  - [*Import Schema (must available DB)*](#import-schema-must-available-db)
  - [*Create DB .sql (Db Not Existed)*](#create-db-sql-db-not-existed)
- [**Export**](#Export)
  - [*Export DB .sql*](#export-db-sql)
  - [*export DB .dump*](#export-db-dump)
  - [*Export Schema Only*](#export-schema-only)
  

## Import
- Role Normal but need cd into bean of `Portgres` and open cmd (`D:\program\PostgreSQL\16\bin`)

#
### Import with .dump
```cmd
pg_restore -U your_username -d target_database backup.dump
```

#
### import DB .sql (DB existed)
```cmd
psql -U your_username -d target_database -f backup.sql
```

**Example:**
```cmd
D:\program\PostgreSQL\16\bin>psql -U postgres -d my_db -f C:\test\backup.sql
```

#
### Import Schema (must available DB)

```cmd
D:\program\PostgreSQL\16\bin>psql -U username -d your_db -f C:\test\test_schema.sql
```

**Example:**
```cmd
D:\program\PostgreSQL\16\bin>psql -U postgres -d my_db -f C:\test\test_schema.sql
```

#
###  Create DB .sql (Db Not Existed)
```cmd
createdb -U your_username target_database
```

**Example:**
```cmd
D:\program\PostgreSQL\16\bin>createdb -U postgres my_db
```


------------------
<br/>

## Export
### Export DB .sql
- open cmd with role `administration`

```cmd
pg_dump -U your_username -h localhost -p 5432 your_database > backup.sql
```

**Example:** 
```cmd
C:\test>pg_dump -U postgres -h localhost -p 5432 my_db > backup.sql
```

#
### export DB .dump
```cmd
pg_dump -U your_username -F c -b -v -f backup.dump your_database
```

**Example:**
```cmd
C:\test>pg_dump -U postgres -F c -b -v -f backup.dump my_db
```

#
### Export Schema Only

```cmd
pg_dump -U your_username -h localhost -p 5432 -n your_schema_name your_database > public_with_data.sql
```

**Example:**
```cmd
C:\test>pg_dump -U postgres -h localhost -p 5432 -n test_schema my_db > test_schema.sql
```

- Import normal:  `D:\program\PostgreSQL\16\bin>psql -U postgres -d my_db -f C:\test\test_schema.sql`
