```sql
CREATE DATABASE company402;
```

```sql
USE company402;
```

```sql
CREATE TABLE employee (
    E_id INT(10) PRIMARY KEY,
    E_name VARCHAR(20),
    Age INT(5),
    Salary FLOAT(10)
);
```

```sql
INSERT INTO employee VALUES
(101,'John',25,20000),
(102,'Sumit',28,15000),
(103,'Ram',30,18000),
(104,'Anu',27,22000),
(105,'Raj',27,25000);
```

```sql
SELECT * FROM employee;
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

```sql
DELIMITER ;
```

```sql
CALL proc_emp();
```
