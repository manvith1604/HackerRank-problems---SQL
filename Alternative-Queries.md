## 1. Draw The Triangle 1

P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):
```
* * * * * 
* * * * 
* * * 
* * 
*
```

Write a query to print the pattern P(20).

Solution: 

```sql
DELIMITER //
CREATE PROCEDURE star(n INT)
BEGIN
    DECLARE i INT DEFAULT 20;
    WHILE i > 0 DO
        SELECT REPEAT('* ', i);
        SET i = i - 1;
    END WHILE;
END //
DELIMITER ;

CALL star(20)
```

## 2. Draw The Triangle 2

P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):
```
* 
* * 
* * * 
* * * * 
* * * * *
```

Write a query to print the pattern P(20).

Solution: 

```sql
DELIMITER //
CREATE PROCEDURE star(n INT)
BEGIN
    DECLARE i INT DEFAULT 1;
    WHILE i < 21 DO
        SELECT REPEAT('* ', i);
        SET i = i + 1;
    END WHILE;
END //
DELIMITER ;

CALL star(20)
```
