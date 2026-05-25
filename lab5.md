```sql
CREATE DATABASE company402;
```

```text
Query OK, 1 row affected (0.00 sec)
```

```sql
USE company402;
```

```text
Database changed
```

```sql
CREATE TABLE employee (
    E_id INT(10) PRIMARY KEY,
    E_name VARCHAR(20),
    Age INT(5),
    Salary FLOAT(10)
);
```

```text
Query OK, 0 rows affected, 2 warnings (0.02 sec)
```

```sql
INSERT INTO employee VALUES
(101,'John',25,20000),
(102,'Sumit',28,15000),
(103,'Ram',30,18000),
(104,'Anu',27,22000),
(105,'Raj',27,25000);
```

```text
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

```sql
SELECT * FROM employee;
```

```text
+------+--------+------+--------+
| E_id | E_name | Age | Salary |
+------+--------+------+--------+
| 101  | John   | 25  | 20000  |
| 102  | Sumit  | 28  | 15000  |
| 103  | Ram    | 30  | 18000  |
| 104  | Anu    | 27  | 22000  |
| 105  | Raj    | 27  | 25000  |
+------+--------+------+--------+
5 rows in set (0.00 sec)
```

```sql
DELIMITER $$
```

```sql
CREATE PROCEDURE proc_emp()
BEGIN
    DECLARE v_ename VARCHAR(20);
    DECLARE v_sal FLOAT;
    DECLARE v_finished INTEGER DEFAULT 0;

    DECLARE c1 CURSOR FOR
    SELECT E_name, Salary FROM employee;

    DECLARE CONTINUE HANDLER FOR NOT FOUND
    SET v_finished = 1;

    OPEN c1;

    get_emp: LOOP

        FETCH c1 INTO v_ename, v_sal;

        IF v_finished = 1 THEN
            LEAVE get_emp;
        END IF;

        SELECT v_ename, v_sal;

    END LOOP get_emp;

    CLOSE c1;

END $$
```

```text
Query OK, 0 rows affected (0.00 sec)
```

```sql
DELIMITER ;
```

```sql
CALL proc_emp();
```

```text
+---------+-------+
| v_ename | v_sal |
+---------+-------+
| John    | 20000 |
+---------+-------+
1 row in set (0.00 sec)

+---------+-------+
| v_ename | v_sal |
+---------+-------+
| Sumit   | 15000 |
+---------+-------+
1 row in set (0.00 sec)

+---------+-------+
| v_ename | v_sal |
+---------+-------+
| Ram     | 18000 |
+---------+-------+
1 row in set (0.00 sec)

+---------+-------+
| v_ename | v_sal |
+---------+-------+
| Anu     | 22000 |
+---------+-------+
1 row in set (0.00 sec)

+---------+-------+
| v_ename | v_sal |
+---------+-------+
| Raj     | 25000 |
+---------+-------+
1 row in set (0.00 sec)

Query OK, 0 rows affected (0.01 sec)
```
