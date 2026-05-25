```sql
CREATE DATABASE company402;
```

```sql
USE company402;
```

```sql
CREATE TABLE employee (
    E_id INT(10) PRIMARY KEY,
    E_name VARCHAR(20) NOT NULL,
    Age INT(5) NOT NULL,
    Salary FLOAT(10) NOT NULL
);
```

```sql
DESC employee;
```

```sql
INSERT INTO employee VALUES (101,'Atharva',20,35000);
```

```sql
INSERT INTO employee VALUES (102,'Sultan',18,42000);
```

```sql
INSERT INTO employee VALUES (103,'Shirdhir',24,22000);
```

```sql
INSERT INTO employee VALUES (104,'Aditya',26,50000);
```

```sql
INSERT INTO employee VALUES (105,'Veeresh',21,55000);
```

```sql
SELECT * FROM employee;
```

```sql
SELECT COUNT(E_name) FROM employee;
```

```sql
SELECT MAX(Age) FROM employee;
```

```sql
SELECT MIN(Age) FROM employee;
```

```sql
SELECT Salary FROM employee ORDER BY Salary;
```

```sql
SELECT Salary FROM employee GROUP BY Salary;
```

```sql
SELECT Salary FROM employee ORDER BY Salary DESC;
```

```sql
SELECT SUM(Salary) FROM employee;
```

```sql
SELECT MAX(Salary) FROM employee;
```

```sql
SELECT MIN(Salary) FROM employee;
```
