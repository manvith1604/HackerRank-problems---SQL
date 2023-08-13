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

## 3. Print Prime Numbers

Write a query to print all prime numbers less than or equal to 1000. Print your result on a single line, and use the ampersand (&) character as your separator (instead of a space).

For example, the output for all prime numbers <10 would be:
```
2&3&5&7
```

Solution: 

```sql
WITH RECURSIVE Numbers AS (
  SELECT 2 AS Number
  UNION ALL
  SELECT Number + 1
  FROM Numbers
  WHERE Number < 1000
)
SELECT GROUP_CONCAT(Number SEPARATOR '&') AS PrimeNumbers
FROM Numbers
WHERE NOT EXISTS (
  SELECT 1
  FROM Numbers AS N
  WHERE N.Number > 1 AND N.Number < Numbers.Number AND Numbers.Number % N.Number = 0);
```


