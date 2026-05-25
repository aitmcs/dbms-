```sql
USE company_db;
```

```sql
DROP TABLE IF EXISTS N_ROLLCALL;
```

```sql
DROP TABLE IF EXISTS O_ROLLCALL;
```

```sql
CREATE TABLE N_ROLLCALL(
    ID INT,
    NAME VARCHAR(100),
    ROLL VARCHAR(100)
);
```

```sql
DESC N_ROLLCALL;
```

```sql
CREATE TABLE O_ROLLCALL(
    ID INT,
    NAME VARCHAR(100),
    ROLL VARCHAR(100)
);
```

```sql
DESC O_ROLLCALL;
```

```sql
INSERT INTO N_ROLLCALL VALUES(123, 'satyal123', '111');
```

```sql
SELECT * FROM N_ROLLCALL;
```

```sql
INSERT INTO O_ROLLCALL VALUES(123, 'satyal123', '110');
```

```sql
SELECT * FROM O_ROLLCALL;
```

```sql
DELIMITER $$
```

```sql
CREATE PROCEDURE ProcessRollcall()
BEGIN

    DECLARE done INT DEFAULT FALSE;
    DECLARE curr_id INT;
    DECLARE curr_name VARCHAR(100);
    DECLARE curr_roll VARCHAR(100);
    DECLARE v_count INT;

    DECLARE c_new_rollcall CURSOR FOR
    SELECT id, name, roll FROM N_ROLLCALL;

    DECLARE CONTINUE HANDLER FOR NOT FOUND
    SET done = TRUE;

    OPEN c_new_rollcall;

    read_loop: LOOP

        FETCH c_new_rollcall
        INTO curr_id, curr_name, curr_roll;

        IF done THEN
            LEAVE read_loop;
        END IF;

        SELECT COUNT(*) INTO v_count
        FROM O_ROLLCALL
        WHERE id = curr_id;

        IF v_count = 0 THEN

            INSERT INTO O_ROLLCALL(id, name, roll)
            VALUES(curr_id, curr_name, curr_roll);

            SELECT CONCAT('Record inserted: ', curr_id)
            AS Action_Taken;

        ELSE

            SELECT CONCAT('Record skipped: ', curr_id)
            AS Action_Taken;

        END IF;

    END LOOP;

    CLOSE c_new_rollcall;

END$$
```

```sql
DELIMITER ;
```

```sql
CALL ProcessRollcall();
```

```sql
SELECT * FROM O_ROLLCALL;
```
