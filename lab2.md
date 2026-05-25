```sql
CREATE DATABASE employee402;
```

```sql
USE employee402;
```

```sql
CREATE TABLE employee (
    Empno INT(10) PRIMARY KEY,
    Ename VARCHAR(50) NOT NULL,
    Job VARCHAR(50) NOT NULL,
    Manager_no INT(20) NOT NULL,
    salary FLOAT(10)
);
```

```sql
DESC employee;
```

```sql
ALTER TABLE employee ADD comission INT(10);
```

```sql
DESC employee;
```

```sql
INSERT INTO employee VALUES
(101,'Atharva','Software Engg',123456,25000,10);
```

```sql
INSERT INTO employee VALUES
(102,'Abcdefg','HR',654321,40000,5);
```

```sql
INSERT INTO employee VALUES
(103,'Sultan','Developer',456789,45000,7);
```

```sql
INSERT INTO employee VALUES
(104,'Adee','Tester',147258,35000,6);
```

```sql
INSERT INTO employee VALUES
(105,'Qwerty','Software Engg',223355,20000,8);
```

```sql
SELECT * FROM employee;
```

```sql
UPDATE employee
SET Job = 'HR'
WHERE Empno = 105;
```

```sql
SELECT * FROM employee;
```

```sql
ALTER TABLE employee
RENAME COLUMN Ename TO Employee_Name;
```

```sql
SELECT * FROM employee;
```

```sql
DELETE FROM employee
WHERE Empno = 105;
```

```sql
SELECT * FROM employee;
```
