```sql
CREATE DATABASE IF NOT EXISTS company_db;
```

```sql
USE company_db;
```

```sql
CREATE TABLE Employee (
    E_id INT PRIMARY KEY,
    E_name VARCHAR(255),
    Age INT,
    Salary DECIMAL(10,2)
);
```

```sql
DESC Employee;
```

```sql
INSERT INTO Employee VALUES (1, 'JOHN', 30, 50000);
```

```sql
INSERT INTO Employee VALUES (2, 'JACK', 40, 60000);
```

```sql
INSERT INTO Employee VALUES (3, 'SHAM', 50, 70000);
```

```sql
SELECT * FROM Employee;
```

```sql
DELIMITER $$
```

```sql
CREATE PROCEDURE GetEmployees()
BEGIN

    DECLARE done INT DEFAULT FALSE;
    DECLARE v_id INT;
    DECLARE v_name VARCHAR(255);
    DECLARE v_age INT;
    DECLARE v_salary DECIMAL(10,2);

    DECLARE employee_cursor CURSOR FOR
    SELECT E_id, E_name, Age, Salary FROM Employee;

    DECLARE CONTINUE HANDLER FOR NOT FOUND
    SET done = TRUE;

    OPEN employee_cursor;

    read_loop: LOOP

        FETCH employee_cursor
        INTO v_id, v_name, v_age, v_salary;

        IF done THEN
            LEAVE read_loop;
        END IF;

        SELECT CONCAT(
            'Employee ID: ', v_id,
            ' Name: ', v_name,
            ' Age: ', v_age,
            ' Salary: ', v_salary
        ) AS Employee_Details;

    END LOOP;

    CLOSE employee_cursor;

END$$
```

```sql
DELIMITER ;
```

```sql
CALL GetEmployees();
```
