```sql
CREATE DATABASE college402;
```

```sql
USE college402;
```

```sql
CREATE TABLE o_rollcall (
    rno INTEGER(20) PRIMARY KEY,
    name VARCHAR(20),
    address VARCHAR(20)
);
```

```sql
INSERT INTO o_rollcall VALUES (1,'John','Belgavi');
```

```sql
INSERT INTO o_rollcall VALUES (2,'Smith','Mumbai');
```

```sql
INSERT INTO o_rollcall VALUES (3,'Joe','Bangalore');
```

```sql
INSERT INTO o_rollcall VALUES (4,'Jack','Delhi');
```

```sql
INSERT INTO o_rollcall VALUES (5,'Atharva','Hyderabad');
```

```sql
SELECT * FROM o_rollcall;
```

```sql
CREATE TABLE n_rollcall (
    rno INTEGER(20),
    name VARCHAR(20),
    address VARCHAR(20)
);
```

```sql
INSERT INTO n_rollcall VALUES (1,'John','Belgavi');
```

```sql
INSERT INTO n_rollcall VALUES (2,'Smith','Mumbai');
```

```sql
INSERT INTO n_rollcall VALUES (3,'Joe','Bangalore');
```

```sql
SELECT * FROM n_rollcall;
```

```sql
DELIMITER $$
```

```sql
CREATE PROCEDURE n1(IN rno1 INT)
BEGIN

    DECLARE rno2 INT;
    DECLARE exit_cond BOOLEAN;

    DECLARE c1 CURSOR FOR
    SELECT rno FROM o_rollcall WHERE rno > rno1;

    DECLARE CONTINUE HANDLER FOR NOT FOUND
    SET exit_cond = TRUE;

    OPEN c1;

    I1 : LOOP

        FETCH c1 INTO rno2;

        IF NOT EXISTS(
            SELECT * FROM n_rollcall WHERE rno = rno2
        ) THEN

            INSERT INTO n_rollcall
            SELECT * FROM o_rollcall WHERE rno = rno2;

        END IF;

        IF exit_cond THEN
            CLOSE c1;
            LEAVE I1;
        END IF;

    END LOOP I1;

END $$
```

```sql
DELIMITER ;
```

```sql
CALL n1(3);
```

```sql
SELECT * FROM n_rollcall;
```
