```sql
CREATE USER 'student'@'localhost' IDENTIFIED BY 'Student@123';
```

```sql
SELECT user FROM mysql.user;
```

```sql
GRANT ALL PRIVILEGES ON *.* TO 'student'@'localhost';
```

```sql
SHOW PRIVILEGES;
```

```sql
CREATE DATABASE company;
```

```sql
SHOW DATABASES;
```

```sql
USE company;
```

```sql
CREATE TABLE employee(
    empno INTEGER(2),
    ename VARCHAR(10),
    job VARCHAR(10),
    manager_no INTEGER(3),
    sal FLOAT(10),
    commission FLOAT(10)
);
```

```sql
DESC employee;
```

```sql
INSERT INTO employee VALUES(1,'jhon','engg',111,500000,10);
```

```sql
INSERT INTO employee VALUES(2,'devid','analyst',222,400000,30);
```

```sql
INSERT INTO employee VALUES(3,'elson','clerk',333,300000,50);
```

```sql
INSERT INTO employee VALUES(4,'joseph','trainee',444,350000,60);
```

```sql
SELECT * FROM employee;
```

```sql
START TRANSACTION;
```

```sql
DELETE FROM employee WHERE empno=4;
```

```sql
ROLLBACK;
```

```sql
SELECT * FROM employee;
```

```sql
ALTER TABLE employee ADD PRIMARY KEY(empno);
```

```sql
DESC employee;
```

```sql
ALTER TABLE employee MODIFY ename VARCHAR(10) NOT NULL;
```

```sql
INSERT INTO employee VALUES(5,'joe','engg',555,NULL,NULL);
```

```sql
SELECT * FROM employee;
```

```sql
INSERT INTO employee VALUES(NULL,'mary','sales',666,35000,60);
```
